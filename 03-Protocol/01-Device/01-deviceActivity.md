---
title: deviceActivity
---

## deviceActivity {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
By default, the device will flash with every request it receives, which can be enabled or disabled using this command

------------------------------------------------------------------------------------------------------------------

### read
Read the current state of the activity flash feature

#### Request
```json
{
  "property": "deviceActivity",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceActivity",
  "result": {
    "enabled": true
  }
}
```

#### Result
- `enabled` - activity flash is enabled `true` or disabled `false`

------------------------------------------------------------------------------------------------------------------

### write
Set the behaviour of the activity light by either enabling or disabling it.

#### Request
```json
{
  "property": "deviceActivity",
  "operation": 1,
  "payload": {
    "enabled": true
  }
}
```

#### Payload
- `enabled` - set the activity flash to be enabled `true` or disabled `false`

#### Response
```json
{
  "success": true,
  "property": "deviceActivity",
  "result": {
    "enabled": true
  }
}
```

#### Result
- `enabled` - activity flash is enabled `true` or disabled `false`