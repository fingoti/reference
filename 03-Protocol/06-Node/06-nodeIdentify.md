---
title: nodeIdentify
---

## nodeIdentify
Instruct a Node to flash its LED so it can be located.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeIdentify",
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
  "property": "nodeIdentify",
  "result": {
    "identify": [
      {
        "serial": "string",
        "value": true
      }
    ]
  }
}
```

#### Result
- `identify` - an array of one or more nodes responses, depending on if a serial was supplied
- `serial` - the device serial number
- `value` - if the node is identifying `true` or not `false`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "nodeIdentify",
  "operation": 1,
  "payload": {
    "serial": "string",
    "identify": true
  }
}
```

#### Payload
- `serial` - serial of the node to write the address to, for example, "A1B2C3D4E5"
- `identify` - set the node to identify, `true` or not, `false`

#### Response
```json
{
  "success": true,
  "property": "nodeIdentify",
  "result": {
    "identify": [
      {
        "serial": "string",
        "value": true
      }
    ]
  }
}
```

#### Result
- `identify` - an array of length one, containing single node response
- `serial` - the device serial number
- `value` - if the node is identifying `true` or not `false`
