---
title: nodeAction
---

## nodeAction 
Use this command to take actions regarding the node module of the device.

------------------------------------------------------------------------------------------------------------------

### write

**restart** - Restart the node to perform a full power cycle

#### Request
```json
{
  "property": "nodeAction",
  "operation": 1,
  "payload": {
    "action": "string"
  }
}
```

#### Payload
- `action` - "restart"

#### Response
```json
{
  "success": true,
  "property": "nodeAction",
  "result": {
    "message": "string"
  }
}
```

#### Result
- `message` - "Node is restarting"

**reset** - Reset the node to erase all settings and restore back to factory default settings

#### Request
```json
{
  "property": "nodeAction",
  "operation": 1,
  "payload": {
    "action": "string"
  }
}
```

#### Payload
- `action` - "reset"

#### Response
```json
{
  "success": true,
  "property": "nodeAction",
  "result": {
    "message": "string"
  }
}
```

#### Result
- `message` - "Node has been reset back to factory default settings"
