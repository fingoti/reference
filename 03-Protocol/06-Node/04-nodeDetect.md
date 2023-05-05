---
title: nodeDetect
---

## nodeDetect
Retrieve a list of Nodes and their properties

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeDetect",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "nodeDetect",
  "result": {
    "detect": [
      {
        "serial": "string",
        "address": 0,
        "static": true,
        "port": 0,
        "position": 0
      }
    ]
  }
}
```

#### Result
- `detect` - an array of none or more nodes responses, depending on number of connected devices
- `serial` - the device serial number
- `address` - the modbus address that the node is currently using on the bus
- `static` - if the address is static or dynamic
- `port` - which port of the gateway the node is connected to, A `0` or B, `1`
- `position` - the position of the node on the Vyne, `1` being the closest and `32` being the furthest away
