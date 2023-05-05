---
title: devicePoke
---

## devicePoke {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
By default, the device will flash blue with every local HTTP, API or Portal request it receives, which can be enabled or disabled using this command.

------------------------------------------------------------------------------------------------------------------

### read
Interrogate the device to receive a response, similar to a ping

#### Request
```json
{
  "property": "devicePoke",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "devicePoke",
  "result": {
    "message": "string"
  }
}
```

#### Result
- `message` - `"OUCH!"`