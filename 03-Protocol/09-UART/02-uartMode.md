---
title: uartMode
---

## uartMode {% deviceBadge device="pebl" /%} 
Set the UART mode to behave in particular ways for your application

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "uartMode",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "uartMode",
  "result": {
    "mode": 0
  }
}
```

#### Result
- `mode` - the current UART mode, interpreter mode `0` or passthrough mode `1`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "uartMode",
  "operation": 1,
  "payload": {
    "mode": 0
  }
}
```

#### Result
- `mode` - set the UART mode to be either interpreter mode `0` or passthrough mode `1`

#### Response
```json
{
  "success": true,
  "property": "uartMode",
  "result": {
    "mode": 0
  }
}
```

#### Result
- `mode` - the current UART mode, interpreter mode `0` or passthrough mode `1`