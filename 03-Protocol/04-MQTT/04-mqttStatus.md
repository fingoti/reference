---
title: mqttStatus
---

## mqttStatus {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Read the current connection status of the MQTT client and read any potential connection failure reasons

------------------------------------------------------------------------------------------------------------------

### read
Returns the current MQTT session status

#### Request
```json
{
  "property": "mqttStatus",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "mqttStatus",
  "result": {
    "enabled": true,
    "connected": true,
    "error": 0
  }
}
```

#### Result
- `enabled` - if MQTT functionality is enabled `true` or not `false`
- `connected` - if the device is connected to an MQTT broker `true` or not `false`
- `error` - an error code for a connection failure

> **NOTE**
>
> Reasons for connection errors:
>
> `0` - Incorrect IP address and/or port
>
> `1` - Incorrect response from the broker
>
> `2` - Could not resolve domain name
>
> `3` - Timed out waiting for a connection acknowledgement
>
> `4` - Failed to send the connect message
>
> `5` - Broker is not at least version 3.1.1
>
> `6` - The client ID was rejected
>
> `7` - The broker is not available
>
> `8` - The username and/or password was not accepted
>
> `9` - The username was unauthorised

------------------------------------------------------------------------------------------------------------------

### write
Enable or disable the MQTT session

#### Request
```json
{
  "property": "mqttStatus",
  "operation": 1,
  "payload": {
    "enabled": true
  }
}
```

#### Payload
- `enabled` - set the MQTT functionality to be enabled `true` or disabled `false`

#### Response
```json
{
  "success": true,
  "property": "mqttStatus",
  "result": {
    "enabled": true,
    "connected": true
  }
}
```

#### Result
- `enabled` - if MQTT functionality is enabled `true` or not `false`
- `connected` - if the device is connected to an MQTT broker `true` or not `false`

&nbsp;