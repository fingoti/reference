---
title: gpioDirection
---

## gpioDirection {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Read or change the current direction of a GPIO or all GPIOs. 

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "gpioDirection",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "gpioDirection",
  "result": {
    "direction": []
  }
}
```

#### Result
- `direction` - an array of all GPIO directions, input, `1`, or output `0`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "gpioDirection",
  "operation": 1,
  "payload": {
    "gpio": 0,
    "value": 0,
    "direction": [],
    "save": true
  }
}
```

#### Payload
- `gpio` - the GPIO number to set direction
- `value` - the direction to set the GPIO, input, `1`, or output `0`.
- `save` - save the current direction setting to memory, applied on boot **(OPTIONAL)**

or

- `direction` - an array of 4 direction values to set the GPIO, input, `1`, or output `0`.
- `save` - save the current direction setting to memory, applied on boot **(OPTIONAL)**

#### Response
```json
{
  "success": true,
  "property": "gpioDirection",
  "result": {
    "direction": []
  }
}
```

#### Result
- `direction` - an array of all GPIO directions, input, `1`, or output `0`

