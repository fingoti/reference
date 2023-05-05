---
title: deviceSerial
---

## deviceSerial {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Read the serial number of the device, used to identify it for claiming on the Portal, for example.

------------------------------------------------------------------------------------------------------------------

### read
Returns the serial number of the device.

#### Request
```json
{
  "property": "deviceSerial",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceSerial",
  "result": {
    "serial": "string"
  }
}
```

#### Result
- `serial` - device's serial number, for example `"A1B2C3D4E5"`