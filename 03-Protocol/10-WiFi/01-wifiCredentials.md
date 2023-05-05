---
title: wifiCredentials
---

## wifiCredentials {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
View or modify the primary and secondary WiFi networks which the Fingoti device will connect to.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "wifiCredentials",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "wifiCredentials",
  "result": {
    "slot": []
  }
}
```

#### Result
- `slot` - an array of up to 2 SSIDs currently stored in the device

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "wifiCredentials",
  "operation": 1,
  "payload": {
    "slot": 0,
    "ssid": "string",
    "password": "string"
  }
}
```

#### Payload
- `slot` - the credentials slot to be written to, either primary, `0` or secondary, `1`
- `ssid` - the ssid of the WiFi access point to connect to. Must be no more than 32 characters in length
- `password` - the password of the WiFi access point to connect to. Must be at least 8 and no more than 64 characters in length

#### Response
```json
{
  "success": true,
  "property": "wifiCredentials",
  "result": {
    "slot": []
  }
}
```

#### Result
- `slot` - an array of up to 2 SSIDs currently stored in the device
