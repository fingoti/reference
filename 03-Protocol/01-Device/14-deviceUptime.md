---
title: deviceUptime.md
---

## deviceUptime {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
The time passed since the device was last powered on can be received using this command.

------------------------------------------------------------------------------------------------------------------

### read
Returns the uptime of the device since last boot.

#### Request
```json
{
  "property": "deviceUptime",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceUptime",
  "result": {
    "uptime": 0,
    "boot": "string"
  }
}
```

#### Result
- `uptime` - device uptime in seconds
- `boot` - UTC timestamp the device booted, but only if a current time ([deviceTime](#deviceTime)) has been set
