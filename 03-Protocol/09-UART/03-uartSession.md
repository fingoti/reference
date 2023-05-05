---
title: uartSession
---

## uartSession {% deviceBadge device="pebl" /%} 
Enable and authenticate the UART session in order to receive push messages

------------------------------------------------------------------------------------------------------------------

### read
Returns the current UART session status

#### Request
```json
{
  "property": "uartSession",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "uartSession",
  "result": {
    "session": true
  }
}
```

#### Result
- `session` - if the current UART session is active `true` or not `false`

------------------------------------------------------------------------------------------------------------------

### write
Enable or disable the UART session

#### Request
```json
{
  "property": "uartSession",
  "operation": 1,
  "payload": {
     "duration": 0,
     "close": true
  }
}
```

#### Payload
- `duration` - the number of minutes the session should be active from `0` to `1440`

or

- `close` - set to `true` to close the current session

> **NOTE:** A duration of 0 minutes will create a session that never expires

#### Response
```json
{
  "success": true,
  "property": "uartSession",
  "result": {
    "session": true,
    "message": "string"
  }
}
```

#### Result
- `session` - if the current UART session is active `true` or not `false`

or

- `message` - `The current session has been closed`
