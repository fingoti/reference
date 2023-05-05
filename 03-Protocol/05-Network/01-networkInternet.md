---
title: networkInternet
---

## networkInternet {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
The device may have successfully connected to a valid WiFi access point, but may not have an active internet connection. Use this command to check if the device has an internet connection or not.

------------------------------------------------------------------------------------------------------------------

### read
Read whether the device has an active internet connection

#### Request
```json
{
  "property": "networkInternet",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "networkInternet",
  "result": {
    "internet": true
  }
}
```

#### Result
- `internet` - if the device has an internet connection, `true` or not `false`
