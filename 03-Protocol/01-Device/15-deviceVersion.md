---
title: deviceVersion
---

## deviceVersion {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
The device hardware version is written to the device at time of manufacture. Use this command to find the devices version.

------------------------------------------------------------------------------------------------------------------

### read
Read the hardware and software version of the device.

#### Request
```json
{
  "property": "deviceVersion",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceVersion",
  "result": {
    "hardware": "string",
    "software": "string"
  }
}
```

#### Result
- `hardware` - device major and minor hardware version, for example, `"01.23"`
- `software` - device major, minor and patch software version, for example, `"01.23.45"`

&nbsp;