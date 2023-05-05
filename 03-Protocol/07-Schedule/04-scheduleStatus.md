---
title: scheduleStatus
---

## scheduleStatus {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Evaluate if the schedule has been enabled. If it is enabled, it will fire. If not, it is still configured for future use, but will not fire.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "scheduleStatus",
  "operation": 0,
  "payload": {
    "slot": 0
  }
}
```

#### Payload
- `slot` - the schedule slot of the status to be read, from `1` to `4`

#### Response
```json
{
  "success": true,
  "property": "scheduleStatus",
  "result": {
    "slot": 0,
    "status": {
        "enabled": true
    }
  }
}
```

#### Result
- `slot` - the slot where the cron string is saved
- `enabled` - schedule is enabled, `true`, or disabled, `false`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "scheduleStatus",
  "operation": 1,
  "payload": {
    "slot": 0,
    "status": {
        "enabled": true
    }
  }
}
```

#### Payload
- `slot` - the schedule slot of the status to be written, from `1` to `4`
- `enabled` - enabled the schedule, `true`, or disable it, `false`

#### Response
```json
{
  "success": true,
  "property": "scheduleStatus",
  "result": {
    "slot": 0,
    "status": {
        "enabled": true
    }
  }
}
```

#### Result
- `slot` - the slot where the status is saved
- `enabled` - schedule is enabled, `true`, or disabled, `false`
