---
title: deviceSleep
---

## deviceSleep {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Put the device into sleep mode, conserving power

------------------------------------------------------------------------------------------------------------------

### write
Set a sleep duration for the device and initiate a sleep action

#### Request
```json
{
  "property": "deviceSleep",
  "operation": 1,
  "payload": {
    "duration": 0
  }
}
```

#### Payload
- `duration` - set the number of seconds for the device to sleep, `1` to `1800`. If omitted, it will sleep forever (OPTIONAL)

#### Response
```json
{
  "success": true,
  "property": "deviceSleep",
  "result": {
    "duration": 0,
    "message": "string"
  }
}
```

#### Result
- `duration` - the number of seconds the device will sleep for
- `message` - `"The device will sleep for 23 seconds"`

