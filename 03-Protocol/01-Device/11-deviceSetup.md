---
title: deviceSetup
---

## deviceSetup {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Determine if the device has already been set up, if not then provide the WiFi network and claim code.

------------------------------------------------------------------------------------------------------------------

### read
Returns the setup state of the device

#### Request
```json
{
  "property": "deviceSetup",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceSetup",
  "result": {
    "setup": true,
    "serial": "string"
  }
}
```

#### Result
- `setup` - if the device has already been set up `true` or not `false`
- `serial` - Device's serial number, for example `"A1B2C3D4E5"`

------------------------------------------------------------------------------------------------------------------

### write
Set up the device by providing the SSID (WiFi network), WiFi password, and claim code from the Portal.

#### Request
```json
{
  "property": "deviceSetup",
  "operation": 1,
  "payload": {
    "ssid": "string",
    "password": "string",
    "code": "string"
  }
}
```

#### Payload
- `ssid` - the SSID of the access point for connecting to
- `password` - the password of the access point for connecting to
- `code` - the 4 character code used to claim the device, for example `"ABCD"`

#### Response
```json
{
  "success": true,
  "property": "deviceSetup",
  "result": {
    "setup": true,
    "message": "string"
  }
}
```

#### Result
- `setup` - if the device has already been set up `true` or not `false`
- `message` - `Attempting to setup the device`
