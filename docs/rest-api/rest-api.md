## Base URL
```
http://gaggiuino.local
```

## REST API Endpoints

### 1. Shots API
---
#### `POST /api/shots`
**Description:**
- Handles shot persistence (streamed upload).
- Used to log espresso shot data.

#### `GET /api/shots/latest`
**Description:**
- Handles retrieving the identifier for the last history shot.

#### `GET /api/shots/*`
**Description:**
- Handles retrieving shot data.
- The wildcard `*` is used to specify individual shot IDs.

#### `DELETE /api/shots/*`
**Description:**
- Deletes a specific shot's data file.
- The wildcard `*` represents the shot ID.
- Requires an SD card to be present.

### 2. Profiles API
---
#### `GET /api/profiles/all`
**Description:**
- Retrieves all available profiles

#### `POST /api/profile-select/*`
**Description:**
- Selects a specific profile.
- The wildcard `*` represents the profile identifier.

#### `DELETE /api/profile-select/*`
**Description:**
- Deletes a specific profile.
- The wildcard `*` represents the profile identifier.

#### `GET /api/profile/*`
**Description:**
- Downloads a single profile's full definition (phases, recipe, stop conditions).
- The wildcard `*` represents the profile identifier.
- REST equivalent of the web UI's profile Export button.

**Response Example:**
```json
{
  "name": "18g Double",
  "waterTemperature": 93,
  "phases": [
    {
      "type": "PRESSURE",
      "skip": false,
      "name": "Preinfusion",
      "target": { "end": 3, "curve": "LINEAR", "time": 5000 },
      "stopConditions": { "time": 10000, "pressureAbove": 4 },
      "restriction": 0
    }
  ],
  "globalStopConditions": { "time": 40000, "weight": 36 },
  "recipe": { "coffeeIn": 18, "coffeeOut": 36, "ratio": 2 }
}
```

**Field Notes:**
- `id` is intentionally omitted so the profile can be re-imported without collisions; a fresh id is assigned on upload.
- Served with `Content-Disposition: attachment` — hitting the URL in a browser downloads a `<name>.json` file.

---
#### `POST /api/profile`
**Description:**
- Creates a new saved profile from a full profile JSON body.
- REST equivalent of the web UI's profile Import button.
- Requires `name` and at least one phase; other missing/malformed fields are filled with zero-value defaults.
- A fresh id is always assigned, regardless of any id in the body.

**Request Body:**
- Same shape as the `GET /api/profile/*` response.

**Success Response:**
```json
{
  "id": 4,
  "name": "18g Double"
}
```

**Error Response:**
- `422` for bad/incomplete JSON, `500` if the profile couldn't be persisted (plain-text body).

### 3. System API
---
#### `GET /api/system/status`
**Description:**
- Handles retrieving the system sensors latest data.

### 4. Settings API
---
#### `GET /api/settings`
**Description:**
- Retrieves all settings in a single response.
- Returns boiler, system, LED, scales, display, theme, and version information.

**Response Example:**
```json
{
  "boiler": { "steamSetPoint": 145, "offsetTemp": 5, ... },
  "system": { "pumpFlowAtZero": 0.5, "timezoneOffsetMinutes": -300, ... },
  "led": { "color": { "R": 255, "G": 128, "B": 0 }, ... },
  "scales": { "forcePredictive": false, "hwScalesEnabled": true, ... },
  "display": { "lcdBrightness": 80, "lcdDarkMode": false, ... },
  "theme": { "colourPrimary": 31, "colourSecondary": 63488 },
  "versions": { "coreVersion": "1.0.0", "frontVersion": "1.0.0", ... }
}
```

---
#### `GET /api/settings/boiler`
**Description:**
- Retrieves boiler-related settings.
- Includes steam set point, temperature offset, heating power, dividers, and operational states.

**Response Example:**
```json
{
  "steamSetPoint": 145,
  "offsetTemp": 5,
  "hpwr": 1200,
  "mainDivider": 2,
  "brewDivider": 4,
  "brewDeltaState": "true",
  "dreamSteamState": "false",
  "startupHeatDelta": 10
}
```

#### `POST /api/settings/boiler`
**Description:**
- Updates boiler settings.
- All fields from GET response should be included in the request body.
- Changes are persisted to NVS and trigger system callbacks.

**Request Body:**
```json
{
  "steamSetPoint": 145,
  "offsetTemp": 5,
  "hpwr": 1200,
  "mainDivider": 2,
  "brewDivider": 4,
  "brewDeltaState": "true",
  "dreamSteamState": "false",
  "startupHeatDelta": 10
}
```

**Success Response:**
```json
{
  "success": true
}
```

---
#### `GET /api/settings/system`
**Description:**
- Retrieves system-level settings.
- Includes pump calibration, timezone, API tokens, services state, WiFi, and release channel.

**Response Example:**
```json
{
  "pumpFlowAtZero": 0.5,
  "timezoneOffsetMinutes": -300,
  "sprofilerToken": "abc123xyz",
  "visualizerToken": "def456uvw",
  "servicesState": true,
  "wifiEnabled": true,
  "releaseChannel": 0,
  "momentarySwitches": false,
  "ungroupHomeTiles": false,
  "alternativeFlush": false,
  "mqttEnabled": false,
  "mqttHost": "",
  "mqttPort": 1883,
  "mqttUsername": "",
  "mqttPassword": "",
  "mqttTopicPrefix": "gaggiuino"
}
```

**Field Notes:**
- `releaseChannel`: 0 = stable, 1 = test, 2 = debug
- `mqtt*`: configures the built-in MQTT client (full details in `MQTT.md`).

#### `POST /api/settings/system`
**Description:**
- Updates system settings.
- All fields from GET response should be included in the request body.
- Changes are persisted to NVS and trigger system callbacks.

**Request Body:**
```json
{
  "pumpFlowAtZero": 0.5,
  "timezoneOffsetMinutes": -300,
  "sprofilerToken": "abc123xyz",
  "visualizerToken": "def456uvw",
  "servicesState": true,
  "wifiEnabled": true,
  "releaseChannel": 0,
  "momentarySwitches": false,
  "ungroupHomeTiles": false,
  "alternativeFlush": false,
  "mqttEnabled": false,
  "mqttHost": "",
  "mqttPort": 1883,
  "mqttUsername": "",
  "mqttPassword": "",
  "mqttTopicPrefix": "gaggiuino"
}
```

**Success Response:**
```json
{
  "success": true
}
```

---
#### `GET /api/settings/theme`
**Description:**
- Retrieves theme color settings.
- Colors are in RGB565 format.

**Response Example:**
```json
{
  "colourPrimary": 31,
  "colourSecondary": 63488
}
```

#### `POST /api/settings/theme`
**Description:**
- Updates theme color settings.
- Colors should be provided in RGB565 format.
- Changes are persisted to NVS and trigger system callbacks.

**Request Body:**
```json
{
  "colourPrimary": 31,
  "colourSecondary": 63488
}
```

**Success Response:**
```json
{
  "success": true
}
```

---
#### `GET /api/settings/display`
**Description:**
- Retrieves display-related settings.
- Includes brightness, dark mode, sleep timeout, and auto-home timeout.

**Response Example:**
```json
{
  "lcdBrightness": 80,
  "lcdDarkMode": "false",
  "lcdSleep": 10,
  "lcdGoHome": 5,
  "lcdCloseOnBrewOff": false,
  "simpleUI": false
}
```

**Field Notes:**
- `lcdBrightness`: Screen brightness (0-100)
- `lcdSleep`: Time in minutes before screen sleeps
- `lcdGoHome`: Time in seconds after shot finishes to close shot graph

#### `POST /api/settings/display`
**Description:**
- Updates display settings.
- All fields from GET response should be included in the request body.
- Changes are persisted to NVS and trigger system callbacks.

**Request Body:**
```json
{
  "lcdBrightness": 80,
  "lcdDarkMode": "false",
  "lcdSleep": 10,
  "lcdGoHome": 5,
  "lcdCloseOnBrewOff": false,
  "simpleUI": false
}
```

**Success Response:**
```json
{
  "success": true
}
```

---
#### `GET /api/settings/scales`
**Description:**
- Retrieves scales-related settings.
- Includes hardware scales, Bluetooth scales, and calibration factors.

**Response Example:**
```json
{
  "forcePredictive": "false",
  "hwScalesEnabled": "true",
  "hwScalesF1": 1000,
  "hwScalesF2": 2000,
  "btScalesEnabled": "false",
  "btScalesAutoConnect": "false",
  "btScalesPinnedMac": "AA:BB:CC:DD:EE:FF"
}
```

**Field Notes:**
- `hwScalesF1`, `hwScalesF2`: Hardware scales calibration factors

#### `POST /api/settings/scales`
**Description:**
- Updates scales settings.
- All fields from GET response should be included in the request body.
- Changes are persisted to NVS and trigger system callbacks.

**Request Body:**
```json
{
  "forcePredictive": "false",
  "hwScalesEnabled": "true",
  "hwScalesF1": 1000,
  "hwScalesF2": 2000,
  "btScalesEnabled": "false",
  "btScalesAutoConnect": "false",
  "btScalesPinnedMac": "AA:BB:CC:DD:EE:FF"
}
```

**Success Response:**
```json
{
  "success": true
}
```

---
#### `GET /api/settings/led`
**Description:**
- Retrieves LED-related settings.
- Includes RGB color, state, disco mode, and time-of-flight sensor configuration.

**Response Example:**
```json
{
  "color": {
    "R": 255,
    "G": 128,
    "B": 0
  },
  "state": "true",
  "disco": "false",
  "tof": {
    "max": 100,
    "min": 10
  }
}
```

**Field Notes:**
- `color`: RGB values (0-255 for each component)
- `tof`: Time-of-flight sensor min/max values

#### `POST /api/settings/led`
**Description:**
- Updates LED settings.
- All fields from GET response should be included in the request body.
- Changes are persisted to NVS and trigger system callbacks.

**Request Body:**
```json
{
  "color": {
    "R": 255,
    "G": 128,
    "B": 0
  },
  "state": "true",
  "disco": "false",
  "tof": {
    "max": 100,
    "min": 10
  }
}
```

**Success Response:**
```json
{
  "success": true
}
```

---
#### `GET /api/settings/versions`
**Description:**
- Retrieves version information for all system components.
- This endpoint is read-only (no POST method available).

**Response Example:**
```json
{
  "coreVersion": "a06f97fd",
  "frontVersion": "a06f97fd",
  "staticVersion": "a06f97fd"
}
```

**Field Notes:**
- `coreVersion`: Dynamically populated from system state
- `frontVersion`: Frontend version
- `staticVersion`: Static assets version

---

## Common Response Formats

### Success Response (POST requests)
```json
{
  "success": true
}
```

### Error Response (POST requests)
```json
{
  "success": false,
  "error": "Description of the error"
}
```

### 5. Maintenance API
---
#### `GET /api/maintenance`
**Description:**
- Retrieves service history the machine tracks automatically (descale/backflush).

**Response Example:**
```json
{
  "lastDescaleTimestamp": 1753900000,
  "shotsSinceDescale": 42,
  "lastBackflushTimestamp": 1753000000,
  "shotsSinceBackflush": 10
}
```

**Field Notes:**
- `*Timestamp` fields are epoch seconds; `0` means never recorded.
- A descale is recorded at 50% cycle progress; a backflush once pressure exceeds 10 bar in flush mode for more than 2 seconds.
- `shotsSince*` counters only count shots meeting the 5s minimum-recording threshold.

### 6. Firmware / OTA API
---
#### `POST /api/firmware/update-all`
**Description:**
- Triggers an update from GitHub releases for both ESP32 and STM32, using `system.releaseChannel`.
- Only *starts* the process — poll `/api/firmware/progress` for status.

**Success Response:**
```json
{ "message": "Update started", "success": true }
```

**Error Response:**
```json
{ "message": "Failed to start update", "success": false }
```

---
#### `GET /api/firmware/progress`
**Description:**
- Polls the progress of an in-flight update.

**Response Example:**
```json
{ "progress": 42, "status": "IN_PROGRESS", "type": "C_FW" }
```

**Field Notes:**
- `status`: `IDLE` | `IN_PROGRESS` | `SUCCESS` | `ERROR`
- `type`: `C_FW` | `F_FW` | `F_FS` (frontend filesystem image)

---
#### `GET /api/health`
**Description:**
- Liveness check — always `200` if the webserver is up.
- Useful after triggering an update: when the device reboots mid-flash or on completion, poll this expecting connection failures while down to detect when it's back.

**Response Example:**
```json
{ "status": "ok" }
```

**Note:** The firmware/OTA endpoints do **not** set the `Access-Control-Allow-Origin` header, unlike the settings endpoints.

## Notes

1. **CORS**: All endpoints include `Access-Control-Allow-Origin: *` header
2. **Persistence**: All POST operations to `/api/settings/*` automatically persist changes to NVS (Non-Volatile Storage)
3. **Callbacks**: Settings updates trigger registered callbacks, notifying other system components of changes
4. **Atomic Updates**: Settings are updated atomically - the entire settings structure is updated and persisted as one operation
5. **Content-Type**: All requests and responses use `application/json`
