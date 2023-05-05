---
title: timerStatus
---

## timerStatus {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Query if the timer is enabled, is one-shot or set to repeat.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "timerStatus",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "timerStatus",
  "result": {
    "status": {
      "enabled": true,
      "repeat": true
    }
  }
}
```

#### Result
- `enabled` - timer is enabled, `true`, or disabled, `false`
- `repeat` - timer is set to repeat, `true`, or one-shot, `false`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "timerStatus",
  "operation": 1,
  "payload": {
    "status": {
      "enabled": true,
      "repeat": true
    }
  }
}
```

#### Payload
- `enabled` - enabled the timer, `true`, or disable it, `false`
- `repeat` - set the timer to repeat, `true`, or as a one-shot, `false`

#### Response
```json
{
  "success": true,
  "property": "timerStatus",
  "result": {
    "status": {
      "enabled": true,
      "repeat": true
    }
  }
}
```

#### Result
- `enabled` - timer is enabled, `true`, or disabled, `false`
- `repeat` - timer is set to repeat, `true`, or one-shot, `false`
