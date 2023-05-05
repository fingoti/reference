---
title: nodePower
---

## nodePower
Evaluate the power draw of Nodes in current, and determine the voltage.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodePower",
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
  "property": "nodePower",
  "result": {
    "power": [
      {
        "serial": "string",
        "voltage": 0,
        "current": 0
      }
    ]
  }
}
```

#### Result
- `power` - an array of one or more nodes responses, depending on if a serial was supplied
- `serial` - the device serial number
- `voltage` - the voltage detected at the node in mV
- `current` - the current the node is drawing in uA
