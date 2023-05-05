---
title: gpioPulse
---

## gpioPulse {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Pulse the GPIO on for a certain length of time.

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "gpioPulse",
  "operation": 1,
  "payload": {
    "gpio": 0,
    "duration": 0
  }
}
```

#### Payload
- `gpio` - the GPIO number to be pulsed
- `duration` - the length of time to pulse in seconds, minimum of 1 and maximum of 30.

#### Response
```json
{
  "success": true,
  "property": "gpioPulse",
  "result": {
    "state": []
  }
}
```

#### Result
- `state` - an array of all GPIO states, high, `1`, or low `0`
