---
title: mqttSetup
---

## mqttSetup {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Configure the MQTT connection as a client to a broker

------------------------------------------------------------------------------------------------------------------

### read
Returns the current MQTT configuration

#### Request
```json
{
  "property": "mqttSetup",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "mqttSetup",
  "result": {
    "host": "string",
    "qos": 0,
    "retain": true,
    "port": 0,
    "secure": true,
    "username": "string"
  }
}
```

#### Result
- `host` - the IP or URL of the host MQTT broker
- `qos` - the quality of service level is `0`, `1` or `2`
- `retain` - if the retain flag is set `true` or not `false`
- `port` - the current port the broker is listening on, from `1` to `65535`
- `secure` - if the connection should be securely established `true` or not `false`
- `username` - the username used for authentication

------------------------------------------------------------------------------------------------------------------

### write
Set and store a new MQTT configuration

#### Request
```json
{
  "property": "mqttSetup",
  "operation": 1,
  "payload": {
    "host": "string",
    "qos": 0,
    "retain": true,
    "port": 0,
    "secure": true,
    "username": "string",
    "password": "string",
    "clear": true
  }
}
```

#### Payload
- `host` - the IP or URL of the host MQTT broker
- `qos` - the quality of service level is `0`, `1` or `2`
- `retain` - if the retain flag is set `true` or not `false`
- `port` - the current port the broker is listening on, from `1` to `65535`
- `secure` - if the connection should be securely established `true` or not `false`
- `username` - the username used for authentication
- `password` - the password used for authentication

or

- `clear` - remove the current configuration `true`

#### Response
```json
{
  "success": true,
  "property": "mqttSetup",
  "result": {
    "host": "string",
    "qos": 0,
    "retain": true,
    "port": 0,
    "secure": true,
    "username": "string",
    "message": "string"
  }
}
```

#### Result
- `host` - the IP or URL of the host MQTT broker
- `qos` - the quality of service level is `0`, `1` or `2`
- `retain` - if the retain flag is set `true` or not `false`
- `port` - the current port the broker is listening on, from `1` to `65535`
- `secure` - if the connection should be securely established `true` or not `false`
- `username` - the username used for authentication

or

- `message` - `All MQTT connection details cleared`
