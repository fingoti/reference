---
title: i2cDetect
---

## i2cDetect {% deviceBadge device="pebl" /%} 
Return all available I2C slave device addresses that are currently on the bus, this will be pushed automatically to the Portal on change

------------------------------------------------------------------------------------------------------------------

### read
Returns the current Portal usage status.

#### Request
```json
{
  "property": "i2cDetect",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "i2cDetect",
  "result": {
    "detect": []
  }
}
```

#### Result
- `detect` - an array of i2c device addresses detected on the bus
