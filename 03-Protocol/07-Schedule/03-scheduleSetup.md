---
title: scheduleSetup
---

## scheduleSetup {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Retrieve information about slots, including the cron string and command objects (requests).

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "scheduleSetup",
  "operation": 0,
  "payload": {
    "slot": 0
  }
}
```

#### Payload
- `slot` - the schedule slot of the status to be read, from `1` to `4` **(OPTIONAL)**

> **NOTE:** Omitting `slot` will return the setup object for all slots

#### Response
```json
{
    "success": true,
    "property": "scheduleSetup",
    "result": {
        "setup": [
            {
                "cron": "string",
                "request": [],
                "status": {
                    "enabled": true
                }
            }
        ]
    }
}
```

#### Result
- `setup` - an array of 1 or more objects, containing the schedule setup slot(s)
- `cron` - the saved cron string for the corresponding schedule slot
- `request` - an array of commands that will execute when the schedule is triggered
- `enabled` - schedule is enabled, `true`, or disabled, `false`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
    "property": "scheduleSetup",
    "operation": 1,
    "payload": {
        "slot": 0,
        "clear": true
    }
}
```

#### Payload
- `slot` - the schedule slot to be cleared, from `1` to `4` **(OPTIONAL)**
- `clear` - clear the schedule back to factory defaults

> **NOTE:** Omitting `slot` will clear the setup for all slots back to factory defaults

#### Response
```json
{
    "success": true,
    "property": "scheduleSetup",
    "result": {
        "setup": [
            {
                "cron": "string",
                "request": [],
                "status": {
                    "enabled": true
                }
            }
        ]
    }
}
```

#### Result
- `setup` - an array of 4 objects, containing the schedule setup slot(s)
- `cron` - the saved cron string for the corresponding schedule slot
- `request` - an array of commands that will execute when the schedule is triggered
- `enabled` - schedule is enabled, `true`, or disabled, `false`

