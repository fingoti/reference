---
title: mqttSession
---

## mqttSession {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Enable and authenticate the MQTT session in order to receive push messages

------------------------------------------------------------------------------------------------------------------

### read
Returns the current MQTT session status

#### Request
```json
{
  "property": "mqttSession",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "mqttSession",
  "result": {
    "session": true
  }
}
```

#### Result
- `session` - if the current MQTT session is active `true` or not `false`

------------------------------------------------------------------------------------------------------------------

### write
Enable or disable the MQTT session

#### Request
```json
{
  "property": "mqttSession",
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
  "property": "mqttSession",
  "result": {
    "session": true,
    "message": "string"
  }
}
```

#### Result
- `session` - if the current MQTT session is active `true` or not `false`

or 

- `message` - `The current session has been closed`
