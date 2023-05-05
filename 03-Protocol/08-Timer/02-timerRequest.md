---
title: timeRequest
---

## timerRequest {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
Save the request that the timer will execute with every trigger

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "timerRequest",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "timerRequest",
  "result": {
    "request": []
  }
}
```

#### Result
- `request` - an array of commands that will execute when the timer is triggered.

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "timerRequest",
  "operation": 1,
  "payload": {
    "request": []
  }
}
```

#### Result
- `request` - an array of commands to execute when the timer is triggered. Maximum of 8 commands.

or

- `clear` - clear the currently saved request with `true`

#### Response
```json
{
  "success": true,
  "property": "timerRequest",
  "result": {
    "request": [],
    "message": "string"
  }
}
```

#### Result
- `request` - an array of commands that will execute when the timer is triggered

or

- `message` - `"Timer request cleared"`
