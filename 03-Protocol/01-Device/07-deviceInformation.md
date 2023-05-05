---
title: deviceInformation
---

## deviceInformation {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
All current device configuration properties are saved internally and can be requested using this command

------------------------------------------------------------------------------------------------------------------

### read
Read the current configuration of the device

#### Request
```json
{
  "property": "deviceInformation",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceInformation",
  "result": {
    "serial": "string"
  }
}
```

#### Result
- `serial` - Device's serial number, for example `"A1B2C3D4E5"`

> **NOTE:** Will only return partial results if the request is unauthorised. May be sent in multiple split messages due to memory restrictions.