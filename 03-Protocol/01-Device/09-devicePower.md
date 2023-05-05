---
title: devicePower
---

## devicePower {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
By default, the device will flash blue with every local HTTP, API or Portal request it receives, which can be enabled or disabled using this command.

------------------------------------------------------------------------------------------------------------------

### read
Read the voltage, current usage and source of the device power

#### Request
```json
{
  "property": "devicePower",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "devicePower",
  "result": {
    "voltage": 0,
    "current": 0,
    "source": 0
  }
}
```

#### Result
- `voltage` - running voltage of the device in millivolts, for example `5320`
- `current` - current being drawn by the device in microamps, for example `8821` **(VYNE ONLY)**
- `source` - whether the device is being powered via mains `0` or battery `1` **(VYNE ONLY)**

------------------------------------------------------------------------------------------------------------------

### write
Restart the device by forcing a power cycle

#### Request
```json
{
  "property": "devicePower",
  "operation": 1,
  "payload": {
    "restart": true
  }
}
```

#### Payload
- `restart` - restart the device, `true`

#### Response
```json
{
  "success": true,
  "property": "devicePower",
  "result": {
    "message": "string"
  }
}
```

#### Result
- `message` - `"Device restarting"`
