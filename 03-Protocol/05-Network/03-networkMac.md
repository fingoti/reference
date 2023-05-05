---
title: networkMac
---

## networkMac {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
This command will return the devices MAC address.

------------------------------------------------------------------------------------------------------------------

### read
Read the devices MAC addresses

#### Request
```json
{
  "property": "networkMac",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "networkMac",
  "result": {
    "station": "string",
    "ap": "string"
  }
}
```

#### Result
- `station` - the MAC address of the device, for example, "A7:D4:8C:92:A0:E3"
- `ap` - the MAC address of the device's access point, for example, "4B:23:A1:02:C7:5A"
