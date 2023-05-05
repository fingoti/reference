---
title: timerInterval
---

## timerInterval {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Set the interval between each trigger of the timer

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "timerInterval",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "timerInterval",
  "result": {
    "interval": 0
  }
}
```

#### Result
- `interval` - the saved interval time between each timer trigger, in seconds

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "timerInterval",
  "operation": 1,
  "payload": {
    "interval": 0
  }
}
```

#### Result
- `interval` - the interval time between each timer trigger, in seconds between `1` and `86400` (24 hours)

#### Response
```json
{
  "success": true,
  "property": "timerInterval",
  "result": {
    "interval": 0
  }
}
```

#### Result
- `interval` - the saved interval time between each timer trigger, in seconds
