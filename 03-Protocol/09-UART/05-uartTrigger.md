---
title: uartTrigger
---

## uartTrigger {% deviceBadge device="pebl" /%} 
Establish the byte offset or terminator to begin sending from.

------------------------------------------------------------------------------------------------------------------

### read
Returns the current configuration of the trigger.

#### Request
```json
{
  "property": "uartTrigger",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "uartTrigger",
  "result": {
    "trigger": {
        "length": 0,
        "terminator": []
    }
  }
}
```

#### Result
- `length` - the number of bytes to wait for before transmitting the data packet from `0` to `256`
- `terminator` - an array of 1 to 16 decimal encoded characters representing the terminator

------------------------------------------------------------------------------------------------------------------

### write
Write the byte offset or terminator (e.g. CR, LF) to use.

#### Request
```json
{
  "property": "uartTrigger",
  "operation": 1,
  "payload": {
    "trigger": {
        "length": 0,
        "terminator": []
    }
  }
}
```

#### Payload
- `length` - the number of bytes to wait for before transmitting the data packet from `0` to `256`
- `terminator` - an array of 1 to 16 decimal encoded characters representing the terminator

> **NOTE:** A length of 0 will default to use of the terminator

#### Response
```json
{
  "success": true,
  "property": "uartTrigger",
  "result": {
    "trigger": {
        "length": 0,
        "terminator": []
    }
  }
}
```

#### Result
- `length` - the number of bytes to wait for before transmitting the data packet from `0` to `256`
- `terminator` - an array of 1 to 16 decimal encoded characters representing the terminator