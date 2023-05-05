---
title: deviceBus
---

## deviceBus {% deviceBadge device="pebl" /%} 
Choose between the different bus protocols for serial communication.

------------------------------------------------------------------------------------------------------------------

### read
Read the current bus protocol

#### Request
```json
{
  "property": "deviceBus",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceBus",
  "result": {
    "protocol": 0
  }
}
```

#### Result
- `protocol` - the current bus protocol, for uart `0` and i2c `1`

------------------------------------------------------------------------------------------------------------------

### write
Set the bus protocol which immediately reconfigures the device

#### Request
```json
{
  "property": "deviceBus",
  "operation": 1,
  "payload": {
    "protocol": 0
  }
}
```

#### Payload
- `protocol` - the desired bus protocol, for uart `0` and i2c `1`

#### Response
```json
{
  "success": true,
  "property": "deviceBus",
  "result": {
    "protocol": 0
  }
}
```

#### Result
- `protocol` - the current bus protocol, for uart `0` and i2c `1`


