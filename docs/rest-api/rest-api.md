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
