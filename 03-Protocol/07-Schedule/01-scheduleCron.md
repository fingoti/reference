---
title: scheduleCron
---

## scheduleCron {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Schedule up to four cron jobs, by using different slots.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "scheduleCron",
  "operation": 0,
  "payload": {
    "slot": 0
  }
}
```

#### Payload
- `slot` - the schedule slot of the cron string to be read, from `1` to `4`

#### Response
```json
{
  "success": true,
  "property": "scheduleCron",
  "result": {
    "slot": 0,
    "cron": "string"
  }
}
```

#### Result
- `slot` - the slot where the cron string is saved
- `cron` - the saved cron string for the corresponding schedule slot

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "scheduleCron",
  "operation": 1,
  "payload": {
    "slot": 0,
    "cron": "string"
  }
}
```

#### Payload
- `slot` - the schedule slot of the cron string to be read, from `1` to `4`
- `cron` - a valid cron string (more information can be found [here](https://en.wikipedia.org/wiki/Cron)) for the schedule, for example `"5 2 * * *"`

#### Response
```json
{
  "success": true,
  "property": "scheduleCron",
  "result": {
    "slot": 0,
    "cron": "string"
  }
}
```

#### Result
- `slot` - the slot where the cron string is saved
- `cron` - the saved cron string for the corresponding schedule slot
