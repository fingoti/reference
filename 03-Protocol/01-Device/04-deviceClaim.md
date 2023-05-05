---
title: deviceClaim
---

## deviceClaim {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Claim the device on the Portal for use with our API

------------------------------------------------------------------------------------------------------------------

### write
Send the specific claim code provided by the Portal in order to claim the device to your organisation.

#### Request
```json
{
  "property": "deviceClaim",
  "operation": 1,
  "payload": {
    "code": "string"
  }
}
```

#### Payload
- `code` - the 4 character code used to claim the device, for example `"ABCD"`

#### Response
```json
{
  "success": true,
  "property": "deviceClaim",
  "result": {
    "code": "string",
    "message": "string"
  }
}
```

#### Result
- `code` - the 4 character code used to claim the device, for example `"ABCD"`
- `message` - `"Requested device claim from the Cloud"`
