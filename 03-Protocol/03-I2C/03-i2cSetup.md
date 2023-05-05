---
title: i2cSetup
---

## i2cSetup {% deviceBadge device="pebl" /%} 
Read or write all available I2C settings

------------------------------------------------------------------------------------------------------------------

### read
Returns the current I2C setup parameters

#### Request
```json
{
  "property": "i2cSetup",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "i2cSetup",
  "result": {
    "setup": {
      "speed": 0,
      "scan": true
    }
  }
}
```

#### Result
- `speed` - the current I2C bus speed in Hz
- `scan` - whether the I2C detect function is automatic `true` or not `false`

------------------------------------------------------------------------------------------------------------------

### write
Write and save the desired I2C setup parameters

#### Request
```json
{
  "property": "i2cSetup",
  "operation": 1,
  "payload": {
      "speed": 0,
      "scan": true
  }
}
```

#### Payload
- `speed` - the desired I2C bus speed in Hz, from `25000` to `1000000` (slow is `100000`, fast is `400000` and fastplus is `1000000`)
- `scan` - automatic I2C detect scanning enabled `true` or disabled `false`

#### Response
```json
{
  "success": true,
  "property": "i2cSetup",
  "result": {
    "setup": {
      "speed": 0,
      "scan": true
    }
  }
}
```

#### Result
- `speed` - the current I2C bus speed in Hz
- `scan` - whether the I2C detect function is automatic `true` or not `false`

&nbsp;