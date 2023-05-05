---
title: deviceCloud
---

## deviceCloud {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Enable or disable the use of the Fingoti Portal. Disabling the portal will prevent the use of Portal functionality with the device.

------------------------------------------------------------------------------------------------------------------

### read
Returns the current Cloud usage status for use with our Portal

#### Request
```json
{
  "property": "deviceCloud",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceCloud",
  "result": {
    "connected": true,
    "enabled": true,
    "reason": 0
  }
}
```

#### Result
- `connected` - the Cloud is currently connected `true` or disconnected `false`
- `enabled` - use of the Cloud is enabled `true` or disabled `false`

> **NOTE:** Reasons for the device disconnecting from the Cloud are:
>
> `0` - Device unexpectedly lost power
>
> `1` - Device was restarted
>
> `2` - Device is going to sleep
>
> `3` - Device is updating
>
> `4` - WiFi was restarted
>
> `5` - Cloud or MQTT settings were changed

------------------------------------------------------------------------------------------------------------------

### write
Set the Cloud usage state for Portal and API use

#### Request
```json
{
  "property": "deviceCloud",
  "operation": 1,
  "payload": {
    "enabled": true
  }
}
```

#### Payload
- `enabled` - set the state of use for the Portal to be enabled `true` or disabled `false`

#### Response
```json
{
  "success": true,
  "property": "deviceCloud",
  "result": {
    "connected": true,
    "enabled": true
  }
}
```

#### Result
- `connected` - the Cloud is currently connected `true` or disconnected `false`
- `enabled` - use of the Portal is enabled `true` or disabled `false`
