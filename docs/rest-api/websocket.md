# WebSocket API

Gaggiuino exposes a WebSocket endpoint served by the same webserver instance as the rest-api.md and MQTT.md. It's the primary channel the bundled web interface and embedded touchscreen UI use for anything that needs to be live (sensor readings, shot graphs, logs) or round-trip a response (profile CRUD, settings).

If you only need to read state or issue occasional commands, the [REST API](rest-api.md) or [MQTT](MQTT.md) are simpler to integrate against - reach for this one when you need push updates or the handful of operations (full profile editing) that aren't exposed anywhere else.

Every frame - in both directions - is a [Protocol Buffers](https://protobuf.dev/) message sent as a binary WebSocket frame (`WEBSOCKET_OP_BINARY`), **not** JSON text. This is the same nanopb-based wire format used for STM32↔ESP32 communication internally. There is no JSON fallback.

## Endpoint

```
ws://<device-ip>/ws
```

## Envelope

Every frame - in both directions - is a `WebSocketMessageDto` (`frontend-controls/webserver/websocket/proto/websocket.proto`):

```protobuf
message WebSocketMessageDto {
    string action = 1;  // routing key, e.g. "d_sensor_snap" or "c_opmode"
    bytes  data   = 2;  // a second, independently-encoded protobuf message
}
```

`action` is a short string that both selects the message type and routes it (see the tables below); `data` is itself a serialized protobuf message whose type depends on `action` - decode the envelope first, then decode `data` using the type the action implies. This double-encoding (a message containing the bytes of another message) is what lets one WebSocket multiplex dozens of unrelated message shapes over a single connection without a giant `oneof`.

To talk to this API you need protobuf bindings generated from this project's own `.proto` files - there's no separate schema/IDL package to install. Generate them for your language of choice (e.g. [`protobuf-ts`](https://github.com/timostamm/protobuf-ts), which is what the bundled web interface uses - see `frontend-controls/web-interface/build_scripts/build_protobuf.js`) from:

```
lib/Common/**/*.proto
frontend-controls/common/**/*.proto
frontend-controls/webserver/**/*.proto
```

The web interface's generated output (`frontend-controls/web-interface/src/proto/*.ts`) and its consumption of it (`frontend-controls/web-interface/src/api/websocket.ts`) are the canonical, always-up-to-date reference implementation - worth reading alongside this document if anything below is ambiguous.

## Connection Behaviour

- **Max 3 concurrent connections** (`websocket::WS_MAX_CONNECTIONS`). A 4th upgrade attempt gets `429 Too Many Requests` instead of a WebSocket upgrade.
- **On connect**, the server proactively pushes five messages on a staggered schedule, so a fresh client doesn't have to ask for its initial state:
  - `250ms`: `d_act_prof` (active profile)
  - `500ms`: `d_settings`
  - `750ms`: `d_prof_dict` (saved profile summaries)
  - `1000ms`: `d_shot_hist_index`
  - `1250ms`: `d_service_log`
- Everything else (sensor stream, shot stream, logs, system state, wifi, scales, esp stats, firmware progress) only arrives once it's asked for (`g_*` actions below) or once something changes.
- **Broadcast vs targeted**: most `d_*` pushes go to *all* connected clients whenever the underlying state changes (e.g. every client sees every sensor tick), not just the client that asked. A few - `g_*` request/response pairs, `d_prof` in response to `g_prof` - go only to the requesting connection.
- Sending an `action` the server doesn't recognise is logged and silently ignored (no error frame). Sending malformed protobuf bytes as `data` is also logged and ignored - the whole envelope is dropped before your handler ever runs.

## WebSocket Messages

### 1. Server → Client (`d_*`, push/data messages)
---

| Action | Payload type | Sent when |
|---|---|---|
| `d_sensor_snap` | `SensorStateSnapshotDto` | Continuously, while sensor data is flowing from the core |
| `d_shot_snap` | `ShotSnapshotDto` | Once per sample during an active shot |
| `d_sys_state` | `SystemStateDto` | On change, and in response to `g_sys_state` |
| `d_act_prof` | `ProfileDto` | On connect, and whenever the active profile changes |
| `d_prof` | `ProfileDto` | In response to `g_prof`, and after `c_new_prof` succeeds |
| `d_prof_dict` | `SavedProfilesDto` | On connect, and in response to `g_prof_dict` |
| `d_settings` | `GaggiaSettingsDto` | On connect, and in response to `g_settings` |
| `d_notif` | `NotificationDto` | Whenever the machine raises a notification (mirrors the on-screen/MQTT ones - see [MQTT.md](MQTT.md#prefixnotification)) |
| `d_desc_progr` | `DescalingProgressDto` | During a descale cycle |
| `d_ble_scls` | `BleConnectedScalesDto` | In response to `g_ble_scls`, and when the connected BLE scale changes |
| `d_wifi_state` | `WiFiConnectionDto` | In response to `g_wifi_state`, and after any wifi command |
| `d_wifi_networks` | `WiFiNetworksDto` | In response to `g_wifi_networks`/`c_wifi_refresh_networks` |
| `d_esp_mem` | `EspStatsDto` | Periodically (ESP32 heap/PSRAM stats) |
| `d_shot_hist_index` | `ShotHistoryIndexDto` | On connect, and whenever shot history changes |
| `d_service_log` | `ServiceLogDto` | On connect, and whenever a descale/backflush is recorded or a shot is counted (see [MQTT.md](MQTT.md#prefixmaintenance-retained)) |
| `d_fw_upd_progr` | `FirmwareUpdateProgressDto` | During an OTA update (see [REST_API.md](REST_API.md#firmware--ota)) |
| `d_log_record` | `LogRecordDto` | Every log line the device emits (remote logging - see below) |
| `d_resp` | `WebSocketResponseDto` | Acknowledges a `c_*` command (see [Responses](#3-responses) below) |

#### `SensorStateSnapshotDto`
**Description:**
- Live sensor readings, using real numbers (contrast with the shot/MQTT/REST-shots wire formats, which are scaled integers).

**Schema:**
```protobuf
message SensorStateSnapshotDto {
  bool brewActive = 1; bool steamActive = 2; bool hotWaterSwitchState = 3;
  float temperature = 4; float waterTemperature = 5; float pressure = 6;
  float pumpFlow = 7; float weightFlow = 8; float weight = 9;
  uint32 waterLevel = 10; bool boilerState = 11; bool brewSwitchActive = 12;
  bool valveState = 13; bool steamValveState = 14; bool valveBState = 15;
  bool steamBoilerRelayState = 16;

  // Raw electrical level of every pin defined in pindef.h - true = HIGH,
  // false = LOW - read directly via digitalRead(), regardless of what's
  // driving the pin (application GPIO, SPI/HX711 bus, pump dimmer).
  bool pinBrewLevel = 17; bool pinSteamLevel = 18; bool pinWaterLevel = 19;
  bool pinRelayLevel = 20; bool pinValveLevel = 21; bool pinValveBLevel = 22;
  bool pinRelayValveBLevel = 23; bool pinSteamValveRelayLevel = 24;
  bool pinSteamBoilerRelayLevel = 25; bool pinZcLevel = 26;
  bool pinDimmerLevel = 27; bool pinThermoCsLevel = 28;
  bool pinThermoClkLevel = 29; bool pinThermoDoLevel = 30;
  bool pinThermoDiLevel = 31; bool pinHx711SckLevel = 32;
  bool pinHx711Dout1Level = 33; bool pinHx711Dout2Level = 34;
}
```

**Field Notes:**
- `boilerState`/`valveState`/`steamValveState`/`valveBState`/`steamBoilerRelayState` are the actual relay/valve-commanded state (not sensor readings - there's no feedback on these, they're plain outputs), useful for confirming a peripheral is actually responding. See the embedded/web UI's Maintenance page.
- `steamValveState`/`steamBoilerRelayState` are currently always `false` on every buildable board (the hardware they target, `PCBV2`, has no corresponding build environment right now).
- `valveBState` is the boiler↔group/tank routing valve (`openValveB()`/`closeValveB()`) and is only ever non-`false` on the Silver Knight board (`coreType` `"STM32U585-PCB-GSK"`) - always `false` elsewhere.
- The `pin*Level` fields are the raw electrical state of every pin defined in `pindef.h`, backing the Maintenance page's "MCU Pins" table. Unlike the commanded-state fields above, these are true low-level GPIO reads, not software tracking, and reflect the pin even when nothing in the app is actively driving it.
- Pins that don't exist on the connected board (`pinValveBLevel`/`pinRelayValveBLevel` outside Silver Knight; `pinSteamValveRelayLevel`/`pinSteamBoilerRelayLevel` unless `PCBV2` was defined for the build) always read `false`, and the Maintenance page hides their rows entirely in that case rather than showing a misleading `LOW` - see `SystemStateDto.pcbV2` below.

#### `ServiceTestCommandDto`
**Description:**
- Carries the Maintenance page's "Component Tests" (briefly activating the pump/valve/valveB/LED to confirm they respond - valveB only shown on Silver Knight boards), triggered via `c_service_test`. Available both on the embedded touchscreen and over WebSocket.

**Schema:**
```protobuf
enum ServiceTestPeripheralDto { PUMP = 0; VALVE = 1; VALVE_B = 2; LED = 3; }
message ServiceTestCommandDto { ServiceTestPeripheralDto peripheral = 1; }
```

**Field Notes:**
- Both entry points funnel through the same `state::triggerServiceTest()` on the ESP32 and the same `onServiceTestCommandReceived()` on the STM32, which actually refuses the request unless the machine is idle (and, for the pump, has water in the tank) - so a web client can't trigger a real actuator while a shot is in progress.
- `VALVE`/`PUMP`/`LED` pulse briefly and revert; `VALVE_B` **toggles** (open↔closed) rather than pulsing, since it's a 3-way diverter, not a momentary solenoid - each request moves it to the other path and leaves it there so the change can actually be confirmed.

#### `ShotSnapshotDto`
**Description:**
- One message per sample during an active shot.
- Unlike `SensorStateSnapshotDto`, these are **x10 scaled integers**, same convention as the shot-history JSON files (see [REST_API.md](REST_API.md#shot-json-shape)).

**Schema:**
```protobuf
message ShotSnapshotDto {
  uint32 timeInShot = 1; uint32 pressure = 2; uint32 pumpFlow = 3;
  uint32 weightFlow = 4; uint32 temperature = 5; uint32 shotWeight = 6;
  uint32 waterPumped = 7; uint32 targetTemperature = 8;
  uint32 targetPumpFlow = 9; uint32 targetPressure = 10;
}
```

#### `SystemStateDto`
**Description:**
- System/status information, pushed on change and in response to `g_sys_state`.

**Schema:**
```protobuf
enum OperationModeDto {
  BREW_AUTO = 0; BREW_MANUAL = 1; FLUSH = 2; DESCALE = 3;
  STEAM = 4; FLUSH_AUTO = 5; HOT_WATER = 6; HOME = 7;
}
message SystemStateDto {
  bool startupInitFinished = 1; bool tofReady = 2; bool isSteamForgottenON = 3;
  bool scalesPresent = 4; OperationModeDto operationMode = 5;
  uint32 timeAlive = 6; string coreVersion = 7; bool tarePending = 8;
  string coreType = 9; // e.g. "STM32U585-PCB-GSK"
  bool thermocoupleFaulted = 10; bool pressureSensorFaulted = 11;
  string thermocoupleFaultReason = 12; string pressureSensorFaultReason = 13;
  bool pcbV2 = 14;
}
```

**Field Notes:**
- `thermocoupleFaultReason`/`pressureSensorFaultReason` describe *why* the corresponding `*Faulted` flag is set (e.g. `"Open circuit"`, `"Short to GND"`, `"Temp above range"`, `"Stuck reading"` for the thermocouple; `"ADS error code: -100"` for the pressure sensor's I2C ADS1x15). Both are empty strings whenever the matching `*Faulted` flag is `false`.
- `pcbV2` reports whether the connected board was built with `PCBV2` defined (the macro gating `steamValveRelayPin`/`steamBoilerRelayPin` in `pindef.h`) - runtime, not compile-time, same reasoning as `coreType`: the ESP32 firmware is shared across every STM32 core variant and can't see the STM32's build-time macros directly. No current PlatformIO environment defines `PCBV2`, so this is always `false` today; the Maintenance page's "MCU Pins" table hides the `steamValveRelayPin`/`steamBoilerRelayPin` rows whenever it is.

#### `NotificationDto`
**Description:**
- Mirrors the notifications shown on the machine's own UI.

**Schema:**
```protobuf
message NotificationDto {
  enum NotificationTypeDto { INFO = 0; SUCCESS = 1; WARN = 2; ERROR = 3; }
  NotificationTypeDto type = 1;
  string message = 2;
}
```

#### `ProfileDto` and related
**Description:**
- The full profile shape (phases, stop conditions, recipe) - the same structure documented as JSON in [REST_API.md](REST_API.md#shot-json-shape), just protobuf-encoded here instead.

**Schema:**
```protobuf
enum PhaseTypeDto { FLOW = 0; PRESSURE = 1; MANUAL = 2; }
enum TransitionCurveDto { EASE_IN_OUT = 0; EASE_IN = 1; EASE_OUT = 2; LINEAR = 3; INSTANT = 4; }

message TransitionDto {
  float start = 1; float end = 2; TransitionCurveDto curve = 3;
  uint32 time = 4; float volume = 5;
}
message PhaseStopConditionsDto {
  uint32 time = 1; float pressureAbove = 2; float pressureBelow = 3;
  float flowAbove = 4; float flowBelow = 5; float weight = 6;
  float waterPumpedInPhase = 7;
}
message PhaseDto {
  PhaseTypeDto type = 1; TransitionDto target = 2; float restriction = 3;
  PhaseStopConditionsDto stopConditions = 4; float waterTemperature = 5;
  string name = 6; bool skip = 7;
}
message GlobalStopConditionsDto {
  uint32 time = 1; float weight = 2; float waterPumped = 3;
  bool switchToManualPressureCtrl = 4; bool switchToManuaFlowCtrl = 5;
}
message BrewRecipeDto { float coffeeIn = 1; float coffeeOut = 2; float ratio = 3; }
message ProfileDto {
  string name = 1; repeated PhaseDto phases = 2;
  GlobalStopConditionsDto globalStopConditions = 3; float waterTemperature = 4;
  BrewRecipeDto recipe = 5; uint32 id = 6;
}
message SavedProfilesDto { repeated SavedProfileDto profiles = 1; } // {id, name} summaries
message ProfileManualDto {
  float pressure = 1; float flow = 2; float restriction = 3;
  optional bool useFlowControl = 4;
}
```

**Field Notes:**
- `ProfileManualDto` is the live setpoint for `BREW_MANUAL` - see `c_upd_manual_prof` below. It's the same message the STM core protocol uses internally (`lib/Common/proto/profile.proto`), not a separate WebSocket-only type.
- `ProfileManualDto.restriction` is accepted but neither the embedded UI's nor the web UI's manual controls currently expose it - both always send `0` (unrestricted).

### 2. Client → Server (commands and requests)
---

Two conventions: `g_*` actions **request** a `d_*` push in response (no `data` payload needed - send an empty `bytes`); `c_*` actions **command** a change and get back a `d_resp` acknowledgement (see [Responses](#3-responses)).

| Action | Kind | Payload type | Effect |
|---|---|---|---|
| `g_sys_state` | request | *(empty)* | → `d_sys_state` |
| `c_opmode` | command | `UpdateSystemStateCommandDto` | Switches operation mode (brew/steam/flush/etc.) - also how you enter/exit `BREW_MANUAL`, see below |
| `c_tare_pend` | command | `UpdateSystemStateCommandDto` | Requests a scale tare |
| `c_upd_manual_prof` | command | `ProfileManualDto` | Sets the live pressure/flow setpoint while in `BREW_MANUAL` |
| `g_ble_scls` | request | *(empty)* | → `d_ble_scls` (currently connected scale) |
| `g_ble_scls_avail` | request | *(empty)* | Starts a BLE scan (no direct response documented here - see `common/ble/ble_scales.h`) |
| `g_settings` | request | *(empty)* | → `d_settings` |
| `c_upd_settings` | command | `GaggiaSettingsDto` | Applies settings **in memory only** - not persisted |
| `c_save_settings` | command | *(empty)* | Persists the currently-applied settings to flash |
| `g_act_prof` | request | *(empty)* | → `d_act_prof` |
| `c_upd_act_prof` | command | `ProfileDto` | Replaces the active profile (in memory) |
| `c_upd_act_prof_id` | command | `WebSocketProfileIdCommandDto` | Switches active profile by ID (same effect as `POST /api/profile-select/{id}`) |
| `c_save_act_prof` | command | *(empty)* | Persists the active profile + its ID to flash |
| `g_prof_dict` | request | *(empty)* | → `d_prof_dict` |
| `g_prof` | request | `WebSocketProfileIdCommandDto` | → `d_prof` for that profile |
| `c_new_prof` | command | `ProfileDto` | Creates a new saved profile |
| `c_upd_prof` | command | `ProfileDto` | Updates an existing saved profile (by `id` in the payload) |
| `c_del_prof` | command | `WebSocketProfileIdCommandDto` | Deletes a saved profile (rejected if it's the active one) |
| `c_reorder_prof` | command | `WebSocketReorderProfileCommandDto` | Moves a profile to a new position in the saved list |
| `c_upd_desc_progr` | command | `DescalingProgressDto` | Pause/resume a descale cycle (only `state` is read: `PAUSED` pauses, anything else resumes) |
| `g_wifi_state` | request | *(empty)* | → `d_wifi_state` |
| `g_wifi_networks` | request | *(empty)* | → `d_wifi_networks` (last scan results) |
| `c_wifi_disconnect` | command | *(empty)* | Disconnects wifi |
| `c_wifi_reset` | command | *(empty)* | Clears saved wifi credentials |
| `c_wifi_connect` | command | `WiFiCredentialsDto` | Connects to a network |
| `c_wifi_refresh_networks` | command | *(empty)* | Starts a new scan; results arrive via `d_wifi_networks` |

#### `UpdateSystemStateCommandDto`
**Description:**
- Shared payload for `c_opmode` and `c_tare_pend`.

**Schema:**
```protobuf
message UpdateSystemStateCommandDto {
  OperationModeDto operationMode = 1;
  bool tarePending = 2;
}
```

**Field Notes:**
- Both `c_opmode` and `c_tare_pend` share this message shape but each handler only reads the one field it cares about - so for `c_tare_pend` you still need to set `operationMode` to *something* (nanopb has no way to omit a non-optional enum field), but it's ignored; only `tarePending` takes effect. Same the other way round for `c_opmode`.

#### `WebSocketProfileIdCommandDto` / `WebSocketReorderProfileCommandDto`
**Schema:**
```protobuf
message WebSocketProfileIdCommandDto { uint32 id = 1; }
message WebSocketReorderProfileCommandDto { uint32 id = 1; uint32 position = 2; }
```

#### Manual brew control
**Description:**
- `BREW_MANUAL` bypasses the active profile and lets a client drive the pump directly, mid-shot - it's what the sliders on both the embedded UI's and web UI's live shot screen use.

**Field Notes:**
- Two steps: send `c_opmode` with `operationMode: BREW_MANUAL` (only takes effect while a shot is actually running - same restriction the UI controls have), then push `c_upd_manual_prof` as often as needed with the live setpoint.
- `useFlowControl` picks which of `pressure`/`flow` is actually applied to the pump (`false` = pressure control, `true` = flow control) - the other value is still accepted and stored, but has no effect until you switch.
- Send `c_opmode` with `BREW_AUTO` to resume normal profile-driven brewing; releasing the brew switch also exits manual mode on its own so a stale setpoint can't leak into the next shot.

#### Settings persistence
**Description:**
- Unlike the REST API's `POST /api/settings/*` (which applies *and* persists in one call), the WebSocket splits this into two steps.

**Field Notes:**
- `c_upd_settings` applies the full `GaggiaSettingsDto` in RAM immediately (so e.g. the display updates) but a device reset would lose it until you also send `c_save_settings`.
- The same split exists for the active profile (`c_upd_act_prof` vs `c_save_act_prof`). This lets a client preview a change (e.g. dragging a brightness slider) before committing it.

### 3. Responses
---

Every `c_*` command gets a `d_resp` (`WebSocketResponseDto`) sent back to *only the requesting connection*, echoing the action it responded to:

```protobuf
enum WebSocketResponseResultDto { SUCCESS = 0; ERROR = 1; }
message WebSocketResponseDto {
  string action = 1;
  WebSocketResponseResultDto result = 2;
  string errorMessage = 3;  // only meaningful when result == ERROR
}
```

**Field Notes:**
- Match `action` against the action you sent to correlate the response, same as the bundled web client does in `frontend-controls/web-interface/src/api/WebSocketAction.ts`.

### 4. Remote Logging
---

`d_log_record` (`LogRecordDto: {message, source}`) mirrors every log line the device's firmware logger emits - this is how the embedded UI's "remote log" screen works when there's no physical serial connection to the STM32/ESP32 available (relevant if you're debugging core-side behaviour and only have network access - see `common/log/log.h`'s `REMOTE_LOG_INIT`).

**Field Notes:**
- It's a firehose with no filtering or subscribe/unsubscribe - once connected, every client gets every line.

## Example (TypeScript, using protobuf-ts)

```ts
import { WebSocketMessageDto } from './proto/websocket';
import { UpdateSystemStateCommandDto, OperationModeDto } from './proto/messages';

const ws = new WebSocket('ws://192.168.1.77/ws');
ws.binaryType = 'arraybuffer';

ws.onmessage = async (ev) => {
  const bytes = new Uint8Array(ev.data instanceof Blob ? await ev.data.arrayBuffer() : ev.data);
  const { action, data } = WebSocketMessageDto.fromBinary(bytes);
  console.log('received', action, data.length, 'bytes');
  // decode `data` with the DTO type implied by `action` - see the table above
};

function send(action: string, data: Uint8Array = new Uint8Array()) {
  const bytes = WebSocketMessageDto.toBinary({ action, data });
  ws.send(bytes);
}

ws.onopen = () => {
  // Switch to STEAM mode
  const cmd = UpdateSystemStateCommandDto.toBinary({
    operationMode: OperationModeDto.STEAM,
    tarePending: false,
  });
  send('c_opmode', cmd);
};
```

## Notes

1. **Binary protobuf, not JSON**: every frame in both directions is a protobuf message sent as a binary WebSocket frame - there is no JSON fallback.
2. **Double-encoded envelope**: decode `WebSocketMessageDto` first, then decode its `data` bytes using the type implied by `action`.
3. **Bindings**: generate protobuf bindings from the project's own `.proto` files; there's no separate schema package to install.
4. **Max 3 concurrent connections**: a 4th upgrade attempt receives `429 Too Many Requests`.
5. **Request/command conventions**: `g_*` requests a matching `d_*` push (empty payload); `c_*` commands a change and is acknowledged by `d_resp`.
6. **Broadcast vs targeted**: most `d_*` pushes go to all connected clients; `g_*` responses and `d_prof` go only to the requesting connection.
7. **Unrecognised/malformed frames**: logged and silently dropped before the handler runs - no error frame is returned.
