---
title: nodeAddress
---

## nodeAddress
Read and write the modbus address that the node is currently set to

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeAddress",
  "operation": 0,
  "payload": {
    "serial": "string"
  }
}
```

#### Payload
- `serial` - optional serial of the node to be read, for example, "A1B2C3D4E5" (if omitted will return values for all connected nodes)

#### Response
```json
{
  "success": true,
  "property": "nodeAddress",
  "result": {
    "address": [
      {
        "value": 0,
        "static": true
      }
    ]
  }
}
```

#### Result
- `address` - an array of one or more nodes responses, depending on if a serial was supplied
- `serial` - the device serial number
- `value` - the modbus address that the node is currently using on the bus
- `static` - if the address is static or dynamic

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "nodeAddress",
  "operation": 1,
  "payload": {
    "serial": "string",
    "address": 0,
    "static": true
  }
}
```

#### Payload
- `serial` - serial of the node to write the address to, for example, "A1B2C3D4E5"
- `address` - set the modbus address of the node, between 1 and 32
- `static` - set if the node address is static, `true` or dynamic, `false`

#### Response
```json
{
  "success": true,
  "property": "nodeAddress",
  "result": {
    "address": [
      {
        "serial": "string",
        "value": 0,
        "static": true
      }
    ]
  }
}
```

#### Result
- `address` - an array of length one, containing single node response
- `serial` - the node's serial number
- `value` - the modbus address that the node is currently using on the bus
- `static` - if the address is static or dynamic
