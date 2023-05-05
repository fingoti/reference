---
title: nodeData
---

## nodeData
Read and write to the data buffer of the node

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeData",
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
  "property": "nodeData",
  "result": {
    "timestamp": 0,
    "data": [
      {
        "serial": "string",
        "value": "string"
      }
    ]
  }
}
```

#### Result
- `data` - an array of one or more nodes responses, depending on if a serial was supplied
- `serial` - the device serial number
- `value` - the data read from the node's buffer, containing 1 or more values separated by a pipe character
- `timestamp` - epoch formatted timestamp of the time of data capture

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "nodeData",
  "operation": 1,
  "payload": {
    "serial": "string",
    "data": "string"
  }
}
```

#### Payload
- `serial` - serial of the node to write the data to, for example, "A1B2C3D4E5"
- `data` - write a string of 1 to 32 characters to the node's data buffer

#### Response
```json
{
  "success": true,
  "property": "nodeData",
  "result": {
    "timestamp": 0,
    "data": [
      {
        "serial": "string",
        "value": "string"
      }
    ]
  }
}
```

#### Result
- `data` - an array of length one, containing single node response
- `serial` - the device serial number
- `value` - the data read from the node's buffer, containing 1 or more values separated by a pipe character
- `timestamp` - epoch formatted timestamp of the time of data capture
