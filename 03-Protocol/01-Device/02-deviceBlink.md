---
title: deviceBlink
---

## deviceBlink {% deviceBadge device="pebl" /%} 
Enable or disable the blinking feature of the LED, choosing a specific blink rate.

------------------------------------------------------------------------------------------------------------------

### read
Read the current blink rate of the device's LED.

#### Request
```json
{
  "property": "deviceBlink",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceBlink",
  "result": {
    "state": 0
  }
}
```

#### Result
- `state` - the speed of the blinking, for off `0`, slow `1`, medium `2`, fast `3` and fastest `4`

------------------------------------------------------------------------------------------------------------------

### write
Set the blink rate of the device's LED.

#### Request
```json
{
  "property": "deviceBlink",
  "operation": 1,
  "payload": {
    "state": 0
  }
}
```

#### Payload
- `state` - the speed of the blinking, for off `0`, slow `1`, medium `2`, fast `3` and fastest `4`

#### Response
```json
{
  "success": true,
  "property": "deviceBlink",
  "result": {
    "state": 0
  }
}
```

#### Result
- `state` - the speed of the blinking, for off `0`, slow `1`, medium `2`, fast `3` and fastest `4`