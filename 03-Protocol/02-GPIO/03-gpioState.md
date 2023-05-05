---
title: gpioState
---

## gpioState {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Read or change the current state of a GPIO or all GPIOs. 

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "gpioState",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "gpioState",
  "result": {
    "state": []
  }
}
```

#### Result
- `state` - an array of all GPIO states, high, `1`, or low `0`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "gpioState",
  "operation": 1,
  "payload": {
    "gpio": 0,
    "value": 0,
    "state": [],
    "save": true
  }
}
```

#### Payload
- `gpio` - the GPIO number to set state
- `value` - the state to set the GPIO, high, `1`, or low `0`
- `save` - save the current state setting to memory, applied on boot **(OPTIONAL)**

or

- `state` - an array of 4 state values to set the GPIO, high, `1`, or low `0`
- `save` - save the current state setting to memory, applied on boot **(OPTIONAL)**

#### Response
```json
{
  "success": true,
  "property": "gpioState",
  "result": {
    "state": []
  }
}
```

#### Result
- `state` - an array of all GPIO directions, high, `1`, or low `0`

