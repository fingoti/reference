---
title: deviceTime
---

## deviceTime {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Read or modify the real-time clock on the device

------------------------------------------------------------------------------------------------------------------

### read
Returns the current time stored on the device

#### Request
```json
{
  "property": "deviceTime",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceTime",
  "result": {
    "time": "string"
  }
}
```

#### Result
- `time` - UTC timestamp of the currently set time on the device

------------------------------------------------------------------------------------------------------------------

### write
Set and store the time to the device

#### Request
```json
{
  "property": "deviceTime",
  "operation": 1,
  "payload": {
    "time": "string"
  }
}
```

#### Payload
- `time` - UTC timestamp to set on the device, for example `"2021-08-12T20:17:46Z"`

#### Response
```json
{
  "success": true,
  "property": "deviceTime",
  "result": {
    "time": "string"
  }
}
```

#### Result
- `time` - UTC timestamp of the currently set time on the device
