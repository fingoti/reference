---
title: nodeSetup
---

## nodeSetup
The configuration of each Node.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeSetup",
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
  "property": "nodeSetup",
  "result": {
    "setup": [
      {
        "serial": "string",
        "value": 0
      }
    ]
  }
}
```

#### Result
- `setup` - an array of one or more nodes responses, depending on if a serial was supplied
- `serial` - the device serial number
- `value` - the current set up configuration as a 16bit integer

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "nodeSetup",
  "operation": 1,
  "payload": {
    "serial": "string",
    "setup": 0
  }
}
```

#### Payload
- `serial` - serial of the node to write the address to, for example, "A1B2C3D4E5"
- `setup` - set up the configuration of the node, as a 16bit integer

#### Response
```json
{
  "success": true,
  "property": "nodeSetup",
  "result": {
    "setup": [
      {
        "serial": "string",
        "value": 0
      }
    ]
  }
}
```

#### Result
- `setup` - an array of length one, containing single node response
- `serial` - the device serial number
- `value` - the current set up configuration as a 16bit integer
