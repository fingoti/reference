---
title: networkIp
---

## networkIp {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
This command will return the current IP address obtained by the device

------------------------------------------------------------------------------------------------------------------

### read
Read the current IP address

#### Request
```json
{
  "property": "networkIp",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "networkIp",
  "result": {
    "dhcp": true,
    "local": "string",
    "public": "string",
    "mask": "string",
    "gateway": "string",
    "dns": "string"
  }
}
```

#### Result
- `dhcp` - if DHCP is enabled `true` or not `false`
- `local` - the local IP address that the device is currently using, for example `"192.168.1.45"`
- `public` - the public IP address that the device is currently using, for example `"234.54.23.7"`
- `mask` -  the subnet mask address, for example `"255.255.255.0"`
- `gateway` - the gateway address, for example `"192.168.1.1"`
- `dns` - the DNS server address, for example `"8.8.8.8"`

------------------------------------------------------------------------------------------------------------------

### write
Set a new IP configuration

#### Request
```json
{
  "property": "networkIp",
  "operation": 1,
  "payload": {
    "dhcp": true,
    "local": "string",
    "mask": "string",
    "gateway": "string",
    "dns": "string"
  }
}
```

#### Payload
- `dhcp` - enable `true` or disable `false`
- `local` - the local IP address to set, for example `"192.168.1.45"` **(OPTIONAL)**
- `mask` -  the subnet mask address to set, for example `"255.255.255.0"` **(OPTIONAL)**
- `gateway` - the gateway address to set, for example `"192.168.1.1"` **(OPTIONAL)**
- `dns` - the DNS server address to set, for example `"8.8.8.8"` **(OPTIONAL)**

#### Response
```json
{
  "success": true,
  "property": "networkIp",
  "result": {
    "dhcp": true,
    "local": "string",
    "public": "string",
    "mask": "string",
    "gateway": "string",
    "dns": "string",
    "message": "string"
  }
}
```

#### Result
- `dhcp` - if DHCP is enabled `true` or not `false`
- `local` - the local IP address that the device is currently using, for example `"192.168.1.45"`
- `public` - the public IP address that the device is currently using, for example `"234.54.23.7"`
- `mask` -  the subnet mask address, for example `"255.255.255.0"`
- `gateway` - the gateway address, for example `"192.168.1.1"`
- `dns` - the DNS server address, for example `"8.8.8.8"`
- `message` - `"Enabling DHCP and restarting device"` or `"Disabling DHCP and restarting network"`
