---
title: scheduleRequest
---

## scheduleRequest {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Define the command objects to be sent on a schedule.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "scheduleRequest",
  "operation": 0,
  "payload": {
    "slot": 0
  }
}
```

#### Payload
- `slot` - the schedule slot of the request to be read, from `1` to `4`

#### Response
```json
{
  "success": true,
  "property": "scheduleRequest",
  "result": {
    "slot": 0,
    "request": []
  }
}
```

#### Result
- `slot` - the slot where the request is saved
- `request` - an array of 1 command that will execute when the schedule is triggered

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "scheduleRequest",
  "operation": 1,
  "payload": {
    "slot": 0,
    "request": []
  }
}
```

#### Payload
- `slot` - the schedule slot of the request to be read, from `1` to `4`
- `request` - an array of 1 command to execute when the schedule is triggered

#### Response
```json
{
  "success": true,
  "property": "scheduleRequest",
  "result": {
    "slot": 0,
    "request": []
  }
}
```

#### Result
- `slot` - the slot where the request is saved
- `request` - an array of 1 command that will execute when the schedule is triggered