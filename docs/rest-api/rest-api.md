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
  "releaseChannel": 0
}
```

**Field Notes:**
- `releaseChannel`: 0 = stable, 1 = test, 2 = debug

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
  "releaseChannel": 0
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
  "lcdGoHome": 5
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
  "lcdGoHome": 5
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
  "btScalesAutoConnect": "false"
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
  "btScalesAutoConnect": "false"
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

## Notes

1. **CORS**: All endpoints include `Access-Control-Allow-Origin: *` header
2. **Persistence**: All POST operations to `/api/settings/*` automatically persist changes to NVS (Non-Volatile Storage)
3. **Callbacks**: Settings updates trigger registered callbacks, notifying other system components of changes
4. **Atomic Updates**: Settings are updated atomically - the entire settings structure is updated and persisted as one operation
5. **Content-Type**: All requests and responses use `application/json`
