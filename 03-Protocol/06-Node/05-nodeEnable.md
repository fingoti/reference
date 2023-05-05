---
title: nodeEnable
---

## nodeEnable
Read the enabled status of individual nodes, or all nodes connected to a Gateway.


------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "nodeEnable",
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
  "property": "nodeEnable",
  "result": {
    "enable": [
      {
        "serial": "string",
        "value": true
      }
    ]
  }
}
```

#### Result
- `enable` - an array of one or more nodes responses, depending on if a serial was supplied
- `serial` - the device serial number
- `value` - if the node is enabled `true` or disabled `false`

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "nodeEnable",
  "operation": 1,
  "payload": {
    "serial": "string",
    "enable": true
  }
}
```

#### Payload
- `serial` - serial of the node to write the address to, for example, "A1B2C3D4E5"
- `enable` - set if the node is enabled, `true` or disabled, `false`

#### Response
```json
{
  "success": true,
  "property": "nodeEnable",
  "result": {
    "enable": [
      {
        "serial": "string",
        "value": true
      }
    ]
  }
}
```

#### Result
- `enable` - an array of length one, containing single node response
- `serial` - the device serial number
- `value` - if the node is enabled `true` or disabled `false`
