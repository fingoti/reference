---
title: mqttCertificate
---

## mqttCertificate {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Store a PEM encoded certificate for SSL security over MQTT

------------------------------------------------------------------------------------------------------------------

### read
Read if there is a PEM encoded certificate stored on the device

#### Request
```json
{
  "property": "mqttCertificate",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "mqttCertificate",
  "result": {
    "certificate": true
  }
}
```

#### Result
- `certificate` - if a certificate is stored `true` or not `false` on the device

------------------------------------------------------------------------------------------------------------------

### write
Store a PEM encoded certificate for SSL authentication over MQTT port 8883

#### Request
```json
{
  "property": "mqttCertificate",
  "operation": 1,
  "payload": {
     "pem": "string",
     "clear": true
  }
}
```

#### Payload
- `pem` - the certificate in PEM format, including whitespace

or

- `clear` - set to `true` to clear the currently saved certificate **(OPTIONAL)**

#### Response
```json
{
  "success": true,
  "property": "mqttCertificate",
  "result": {
    "certificate": true,
    "message": "string"
  }
}
```

#### Result
- `certificate` - if a certificate is stored `true` or not `false` on the device
- `message` - `"MQTT certificate cleared"`
