---
title: i2cData
---

## i2cData {% deviceBadge device="pebl" /%} 
Write an array of bytes to your I2C component. Up to a maximum of 32 bytes. Longer writes will require sending 2 write commands. 

------------------------------------------------------------------------------------------------------------------

### write
Write an array of bytes to your I2C component. Up to a maximum of 32 bytes. (I2C Profile Builder) Longer writes will require sending 2 write commands. 

#### Request
```json
{
  "property": "i2cData",
  "operation": 1,
  "payload": {
     "address": 0,
     "profile": []
  }
}
```

#### Payload
- `address` - the address of the i2c device to communicate with as a decimal representation between `0` and `255`
- `profile` - write an array of strings that build up an I2C profile

#### Response
```json
{
  "success": true,
  "property": "i2cData",
  "result": {
    "data": []
  }
}
```

#### Result
- `data` - a nested array of arrays containing the read data bytes in decimal format
