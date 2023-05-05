---
title: wifiDetect
---

## wifiDetect {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Looks for nearby (and connected) WiFi networks, displays the signal strength.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "wifiDetect",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "wifiDetect",
  "result": {
    "message": "string",
    "detect": [
      {
        "ssid": "string",
        "signal": 0
      }
    ]
  }
}
```

#### Result
- `message` - `"Searching for nearby access points"`
- `ssid` - the nearby SSID the device has detected
- `signal` - the signal strength of the SSID as a percentage

> **NOTE:** The `detect` array of objects containing the detected WiFi SSIDs and signal strengths will be pushed once the search has finished
>
> The Push (which is different from a response, as the Fingoti device is replying asynchronously) can be viewed from the Portal, in the Command Log.
