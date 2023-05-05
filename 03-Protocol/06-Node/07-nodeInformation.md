---
title: nodeInformation
---

## nodeInformation
Read properties of the Node. Including versioning, addressing, and more.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeInformation",
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
  "property": "nodeInformation",
  "result": {
    "information": [
      {
        "serial": "string",
        "address": 0,
        "static": true,
        "enable": true,
        "identify": true,
        "part": "string",
        "version": {
          "hardware": "string",
          "software": "string"
        },
        "location": {
          "position": 0,
          "port": 0
        },
        "pin": [],
        "data": "string"
      }
    ],
    "timestamp": 0,
    "message": "string"
  }
}
```

#### Result
- `information` - an array of length one, containing single node response
- `serial` - the device serial number
- `address` - the modbus address that the node is currently using on the bus
- `static` - if the address is static or dynamic
- `part` - the part number of the node
- `version` - an object containing the hardware and software versions of the node
- `hardware` - the major and minor hardware versions of the node
- `software` - the major, minor and patch software versions of the node
- `port` - which port of the gateway the node is connected to, A `0` or B, `1`
- `position` - the position of the node on the Vyne, `1` being the closest and `32` being the furthest away
- `enable` - if the node is enabled, `true` or not, `false`
- `identify` - if the node is identifying, `true` or not, `false`
- `pin` - an array of 16 pin states
- `data` - the current contents of the node's data buffer
- `timestamp` - epoch formatted timestamp of the current time

or

- `message` - if no serial was supplied, the message will read "The Portal has been updated with the latest Node information"
