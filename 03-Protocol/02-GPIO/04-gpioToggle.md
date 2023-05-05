---
title: gpioToggle
---

## gpioToggle {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Toggle a GPIO or all GPIOs to invert their current state

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "gpioToggle",
  "operation": 1,
  "payload": {
    "gpio": 0
  }
}
```

#### Payload
- `gpio` - the GPIO number to toggle. If omitted, all GPIOs will toggle **(OPTIONAL)**

#### Response
```json
{
  "success": true,
  "property": "gpioToggle",
  "result": {
    "state": []
  }
}
```

#### Result
- `state` - an array of all GPIO states, high, `1`, or low `0`

&nbsp;