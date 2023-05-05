---
title: uartSession
---

## uartSetup {% deviceBadge device="pebl" /%} 
UART devices must use the same configuration in order to communicate. The current configuration can be read or written.

------------------------------------------------------------------------------------------------------------------

### read
Read the current UART configuration.

#### Request
```json
{
  "property": "uartSetup",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "uartSetup",
  "result": {
    "setup": {
        "baudrate": 0,
        "databits": 0,
        "parity": 0,
        "stopbits": 0
    }
  }
}
```

#### Result
- `baudrate` - the currently set baudrate
- `databits` - the stored number of databits
- `parity` - none `0`, odd `1` or even `2`
- `stopbits` - either 1 `0`, 1.5 `1` or 2 `2`

------------------------------------------------------------------------------------------------------------------

### write
Write the current UART configuration.

#### Request
```json
{
  "property": "uartSetup",
  "operation": 1,
  "payload": {
    "setup": {
        "baudrate": 0,
        "databits": 0,
        "parity": 0,
        "stopbits": 0
    }
  }
}
```

#### Payload
- `baudrate` - a value of `300`, `600`, `1200`, `2400`, `4800`, `9600`, `19200`, `31250`, `38400`, `57600`, `74880`, `115200`, `230400`, `256000`, `460800`, `921600`, `1843200` or `3686400`
- `databits` - either `5`, `6`, `7` or `8`
- `parity` - none `0`, odd `1` or even `2`
- `stopbits` - either 1 `0`, 1.5 `1` or 2 `2`

#### Response
```json
{
  "success": true,
  "property": "uartSetup",
  "result": {
    "setup": {
        "baudrate": 0,
        "databits": 0,
        "parity": 0,
        "stopbits": 0
    }
  }
}
```

#### Result
- `baudrate` - the currently set baudrate
- `databits` - the stored number of databits
- `parity` - none `0`, odd `1` or even `2`
- `stopbits` - either 1 `0`, 1.5 `1` or 2 `2`
