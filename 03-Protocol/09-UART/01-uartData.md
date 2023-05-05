---
title: uartData
---

## uartData {% deviceBadge device="pebl" /%} 
Write data bytes to the serial bus when in passthrough mode.

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "uartData",
  "operation": 1,
  "payload": {
    "data": []
  }
}
```

#### Result
- `data` - an array of data bytes (1024 maximum) in decimal format between `0` and `255`

#### Response
```json
{
  "success": true,
  "property": "uartData",
  "result": {
    "message": "string"
  }
}
```

#### Result
- `message` - `"UART data written to serial bus"`
