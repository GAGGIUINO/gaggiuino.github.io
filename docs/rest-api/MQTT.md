# MQTT

Gaggiuino can connect to an MQTT broker as a **client**, publishing live machine telemetry and accepting a small set of remote-control commands. This runs in addition to, not instead of, the existing HTTP REST API and WebSocket interfaces - all three run side by side.

Gaggiuino does **not** host an MQTT broker itself. You need an existing broker on your network - e.g. [Mosquitto](https://mosquitto.org/), or the broker built into [Home Assistant](https://www.home-assistant.io/integrations/mqtt/) (via the Mosquitto broker add-on). Gaggiuino connects out to it, the same way Home Assistant and any other client on the broker does.

## Requirements

- WiFi connectivity configured and working.
- A reachable MQTT broker (host + port), with credentials if the broker requires authentication.

## Configuration

MQTT settings live in the shared settings struct, so they're kept in sync and can be edited from any of these three places:

- **Embedded touchscreen UI** - Settings → System → MQTT
- **Web interface** - Settings → System → MQTT
- **REST API** - `GET`/`POST` `/api/settings/system`

| Setting | Description | Default |
|---|---|---|
| Enabled | Turns the MQTT client on/off | `false` |
| Host | Broker hostname or IP | *(empty)* |
| Port | Broker port | `1883` |
| Username | Broker username (optional) | *(empty)* |
| Password | Broker password (optional) | *(empty)* |
| Topic prefix | Prefix used for all published/subscribed topics | `gaggiuino` |

**Field Notes:**
- If host is empty, or the connection is disabled, the client makes no connection attempts.
- Editing any of the fields above while connected causes Gaggiuino to disconnect and reconnect with the new settings automatically - no reboot required.

## Connection Behaviour

- **Client ID**: `gaggiuino-<mac-address>` - stable across reconnects, so the broker treats reconnects as the same client/session rather than a new one.
- **Clean session**: yes.
- **Keepalive**: 30 seconds.
- **Reconnection**: if the connection drops (or settings change), Gaggiuino retries every 5 seconds while MQTT remains enabled.
- **QoS**: all publishes and the command subscription use QoS 0.

---

## Published Topics

All topics below are prefixed with your configured topic prefix (default `gaggiuino`), e.g. `gaggiuino/sensors`. Payloads are JSON unless noted otherwise.

### 1. Availability
---
#### `<prefix>/status` *(retained)*
**Description:**
- Retained availability topic so you can tell whether the device is online, including detecting an unclean disconnect (crash, power loss, WiFi drop).
- Plain text payload (`online` / `offline`), not JSON.

| Topic | Payload | Retained |
|---|---|---|
| `<prefix>/status` | `online` / `offline` | yes |

**Field Notes:**
- `offline` is registered as the connection's LWT (Last Will and Testament), delivered by the broker if Gaggiuino disconnects without saying goodbye.
- `online` is published explicitly right after a successful connect.

### 2. Sensors
---
#### `<prefix>/sensors` *(retained)*
**Description:**
- Live sensor readings, published continuously while the shot/brew loop is running.
- Rate-limited to 1Hz on the MQTT side (the embedded/web UI still get every update over the local link) to avoid flooding the broker and, for Home Assistant users, its recorder database.

**Payload Example:**
```json
{
  "brewActive": false,
  "steamActive": false,
  "hotWaterActive": false,
  "temperature": 93.2,
  "waterTemperature": 21.4,
  "pressure": 0.0,
  "pumpFlow": 0.0,
  "weightFlow": 0.0,
  "weight": 0.0,
  "waterLevel": 78,
  "boilerOn": true,
  "valveOpen": false,
  "steamValveOn": false,
  "valveBOpen": false,
  "steamBoilerRelayOn": false
}
```

**Field Notes:**
- `boilerOn`/`valveOpen`/`steamValveOn`/`valveBOpen`/`steamBoilerRelayOn` are the actual relay/valve-commanded state (not sensor readings - there's no hardware feedback on these, they're plain outputs), useful for confirming a peripheral is actually responding. Same live values shown on the embedded/web UI's Maintenance page.
- `steamValveOn`/`steamBoilerRelayOn` are currently always `false` on every buildable board (their hardware target, `PCBV2`, has no corresponding build environment right now).
- `valveBOpen` is the boiler↔group/tank routing valve and is only ever non-`false` on the Silver Knight board (`coreType` `"STM32U585-PCB-GSK"`) - always `false` on every other board.
- The Maintenance page's "MCU Pins" table (raw HIGH/LOW level of every pin defined in `pindef.h`, for wiring diagnostics) is **not** published over MQTT - it's low-level troubleshooting data, not device state useful to home automation. It's available over WebSocket (`SensorStateSnapshotDto`'s `pin*Level` fields - see [WEBSOCKET.md](WEBSOCKET.md#key-payload-shapes)) and shown on both UIs' Maintenance page.

### 3. System
---
#### `<prefix>/system` *(retained)*
**Description:**
- System/status information.

**Payload Example:**
```json
{
  "operationMode": "BREW_AUTO",
  "startupInitFinished": true,
  "tofReady": true,
  "scalesPresent": false,
  "timeAliveSec": 1234,
  "coreVersion": "1.5.0",
  "tarePending": false,
  "thermocoupleFaulted": false,
  "pressureSensorFaulted": false,
  "thermocoupleFaultReason": "",
  "pressureSensorFaultReason": ""
}
```

**Field Notes:**
- `operationMode` is one of: `BREW_AUTO`, `BREW_MANUAL`, `FLUSH`, `DESCALE`, `STEAM`, `FLUSH_AUTO`, `HOT_WATER`, `HOME`.
- `thermocoupleFaulted`/`pressureSensorFaulted` flag a sensor read failure (open/shorted thermocouple, or the pressure sensor's I2C ADC unreachable/erroring) - same diagnostics shown on the embedded/web UI's Maintenance page.
- `thermocoupleFaultReason`/`pressureSensorFaultReason` give the specific cause (e.g. `"Open circuit"`, `"Short to GND"`, `"Temp above range"`, `"Stuck reading"`, or `"ADS error code: -100"`) and are empty strings whenever the matching `*Faulted` flag is `false`.
- There is no MQTT/REST equivalent of the Maintenance page's "Component Tests" (pump/valve/valveB/LED activation buttons, valveB only on Silver Knight boards) - those are available on the embedded touchscreen and over WebSocket (`c_service_test`), but deliberately not over MQTT/REST. See [WEBSOCKET.md](WEBSOCKET.md#key-payload-shapes).

### 4. Shot
---
#### `<prefix>/shot`
**Description:**
- Published during an active shot, one message per sample.

**Payload Example:**
```json
{
  "timeInShotMs": 4200,
  "pressure": 9.1,
  "pumpFlow": 2.1,
  "weightFlow": 1.9,
  "temperature": 93.4,
  "shotWeight": 18.2,
  "waterPumped": 21.5,
  "targetTemperature": 93.0,
  "targetPumpFlow": 2.0,
  "targetPressure": 9.0
}
```

### 5. Active Profile
---
#### `<prefix>/profile/active` *(retained)*
**Description:**
- Published whenever the active profile changes, and retained so a client that subscribes late immediately learns the current profile.

**Payload Example:**
```json
{ "id": 3, "name": "18g Double", "waterTemperature": 93 }
```

**Field Notes:**
- `waterTemperature` is the profile's configured brew target, not a live reading - pair it with `<prefix>/sensors`' `temperature` (the actual boiler reading) for a "reached target temperature" automation.
- It's published here rather than on `<prefix>/shot` specifically so it's available at all times (retained, and not tied to a shot being in progress) - see the Home Assistant section below.

### 6. Maintenance
---
#### `<prefix>/maintenance` *(retained)*
**Description:**
- Service history the machine tracks on its own - when it was last descaled/backflushed, and how many shots have been pulled since.

**Payload Example:**
```json
{
  "lastDescaleTimestamp": 1753900000,
  "shotsSinceDescale": 42,
  "lastBackflushTimestamp": 1753000000,
  "shotsSinceBackflush": 10
}
```

**Field Notes:**
- `*Timestamp` fields are epoch seconds (`0` means "never recorded").
- A descale is recorded once the descale cycle reaches 50% progress; a backflush is recorded once pressure exceeds 10 bar while in a flush mode (a plain purge with no blind filter never gets there, so this is what tells a real backflush apart from just running water through the group).
- Both `shotsSince*` counters only count shots that meet the same minimum-recording-length threshold shot history itself uses (5s).
- See [REST_API.md](REST_API.md#maintenance) for the equivalent REST endpoint, and the embedded/web UI's Maintenance page for a human-readable view.

### 7. Notification
---
#### `<prefix>/notification`
**Description:**
- Mirrors the notifications shown on the machine's own UI.

**Payload Example:**
```json
{ "type": "WARN", "message": "Low water level" }
```

**Field Notes:**
- `type` is one of: `INFO`, `SUCCESS`, `WARN`, `ERROR`.

---

## Command Topics (subscribed)

Gaggiuino subscribes to `<prefix>/cmd/#` and accepts the commands below. Invalid or unrecognised commands are logged and ignored - they don't crash or disconnect the client.

#### `<prefix>/cmd/profile/select`
**Description:**
- Switches the active profile to the given profile ID.

**Payload:**
```json
{ "id": 3 }
```

---
#### `<prefix>/cmd/opmode`
**Description:**
- Switches operation mode. Accepts the same values as `operationMode` in `<prefix>/system`.

**Payload:**
```json
{ "mode": "STEAM" }
```

---
#### `<prefix>/cmd/tare`
**Description:**
- Requests a scale tare.

**Payload:**
- Any/empty.

---
#### `<prefix>/cmd/manual`
**Description:**
- Sets the live pressure/flow setpoint while in `BREW_MANUAL`.

**Payload:**
```json
{ "pressure": 9.0, "flow": 2.0, "useFlowControl": false }
```

### Manual brew control

`BREW_MANUAL` bypasses the active profile and lets you drive the pump directly, mid-shot - the same feature exposed by sliders on the embedded UI's and web UI's live shot screen. Two steps:

1. **Switch into manual mode:** `cmd/opmode` with `{"mode": "BREW_MANUAL"}`. Only takes effect while a shot is actually running (brew switch held) - same restriction the UI controls have.
2. **Push setpoints** as often as you like via `cmd/manual`. `useFlowControl` picks which of `pressure`/`flow` is actually applied (`false` = pressure control, `true` = flow control) - the other value is still accepted and stored, but ignored by the pump until you switch. There's currently no way to set a flow/pressure *restriction* over MQTT - it's always sent unrestricted, same as both UIs.

Switch back to `BREW_AUTO` (`cmd/opmode` with `{"mode": "BREW_AUTO"}`) to resume normal profile-driven brewing; releasing the brew switch also exits manual mode on its own so a stale setpoint can't leak into the next shot.

```bash
# Enter manual mode, then hold at 6 bar
mosquitto_pub -h 192.168.1.50 -t 'gaggiuino/cmd/opmode' -m '{"mode":"BREW_MANUAL"}'
mosquitto_pub -h 192.168.1.50 -t 'gaggiuino/cmd/manual' -m '{"pressure":6,"flow":0,"useFlowControl":false}'

# Switch to flow control at 2.5 mL/s
mosquitto_pub -h 192.168.1.50 -t 'gaggiuino/cmd/manual' -m '{"pressure":0,"flow":2.5,"useFlowControl":true}'
```

---

## Home Assistant

Gaggiuino auto-discovers itself in Home Assistant - no `configuration.yaml` entities to write by hand. As soon as MQTT is enabled and connects, it publishes a single retained [device discovery](https://www.home-assistant.io/integrations/mqtt/#device-discovery-payload) config message to `homeassistant/device/gaggiuino_<mac>/config`, describing every entity below purely in terms of the plain `<prefix>/*` topics above - those topics and payloads are completely unchanged by this, so anything already consuming them (a dashboard, `mosquitto_sub`, a script) is unaffected.

The discovery message is re-published automatically whenever Home Assistant's own MQTT integration restarts (it announces `online` on `homeassistant/status`), and removed (an empty retained payload, deleting the device and all its entities) as soon as MQTT is disabled in Settings.

**Discovered entities:**

| Entity | Topic | Notes |
|---|---|---|
| Boiler temperature, Water temperature, Pressure, Pump flow, Weight flow, Weight, Water level | `sensors` | |
| Brewing, Steaming, Hot water, Boiler heating | `sensors` | binary sensors |
| Operation mode | `system` | `select`; writes to `cmd/opmode` |
| Uptime, Core version *(diagnostic)* | `system` | |
| Scales connected, Water sensor ready *(diagnostic)* | `system` | binary sensors |
| Active profile | `profile/active` | |
| Target temperature | `profile/active` | the active profile's configured brew target, not a live reading - always available (not tied to a running shot), not diagnostic, enabled by default. See below. |
| Tare scales | `cmd/tare` | `button` |
| Notification | `notification` | `event`, shows up in the HA logbook |
| Shot time, Shot weight, Water pumped | `shot` | |
| Target pressure, Target pump flow *(diagnostic, disabled by default)* | `shot` | update at the same rate as the live shot chart (unthrottled, unlike `sensors`); left disabled so they don't flood the recorder unless explicitly enabled |

**Field Notes:**
- `Target temperature` is deliberately *not* sourced from `shot` like the other `target*` entities: `shot`'s `targetTemperature` only exists while a shot is actively running and isn't retained, so it would sit on `unknown` between shots - exactly when a "boiler reached target temperature, go make coffee" automation needs it most. Compare it against `Boiler temperature` (from `sensors`) to build that automation.
- The device card links back to the machine's own web UI (`http://<device-ip>`) via Home Assistant's configuration URL.

---

## Example: testing with mosquitto clients

Assuming a broker at `192.168.1.50:1883` and the default `gaggiuino` prefix:

```bash
# Watch everything Gaggiuino publishes
mosquitto_sub -h 192.168.1.50 -t 'gaggiuino/#' -v

# Switch to profile 3
mosquitto_pub -h 192.168.1.50 -t 'gaggiuino/cmd/profile/select' -m '{"id":3}'

# Start a flush
mosquitto_pub -h 192.168.1.50 -t 'gaggiuino/cmd/opmode' -m '{"mode":"FLUSH"}'

# Tare the scale
mosquitto_pub -h 192.168.1.50 -t 'gaggiuino/cmd/tare' -m ''
```

---

## Troubleshooting

- **Never connects**: confirm the host/port are reachable from the Gaggiuino's network (same subnet/VLAN, no firewall blocking the broker port), and that Enabled is turned on.
- **Connects then immediately disconnects**: check username/password - the broker log will usually show an authentication failure.
- **Settings changes don't seem to apply**: Gaggiuino detects config changes and reconnects automatically within a few seconds; if it doesn't, confirm the settings actually saved (check the same values via `/api/settings/system`).
- **`<prefix>/status` stuck on `offline`**: the device hasn't completed a clean connect since the broker last restarted, or WiFi is down - check the device's own connectivity first.
- **Device/entities don't appear in Home Assistant**: MQTT connecting successfully doesn't guarantee the discovery payload was accepted - Home Assistant validates it and silently drops anything malformed rather than surfacing an error in the UI. Check **Settings → System → Logs** (or enable `logger: logs: homeassistant.components.mqtt: debug`) for a `MQTT discovery schema violation` / `extra keys not allowed` type message, and use an MQTT client (e.g. MQTT Explorer, or `mosquitto_sub -t 'homeassistant/#' -v`) to inspect the raw retained payload on `homeassistant/device/gaggiuino_<mac>/config` against what the log says was rejected.

---

## Notes

1. **Client, not broker**: Gaggiuino connects out to an existing broker; it does not host one.
2. **Runs alongside REST/WebSocket**: MQTT is additive - the HTTP REST API and WebSocket interfaces remain fully available.
3. **Payloads**: JSON unless noted otherwise; `<prefix>/status` is plain text.
4. **Retained topics**: `sensors`, `system`, `profile/active`, `maintenance`, and `status` are retained so late subscribers immediately get current state.
5. **Command subscription**: Gaggiuino subscribes to `<prefix>/cmd/#`; unrecognised commands are logged and ignored.
