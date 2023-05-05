---
title: wifiStatus
---

## wifiStatus {% deviceBadge device="pebl" /%}   {% deviceBadge device="vyne" /%} 
If the device had issues connecting to a WiFi network, you can view the error code and restart the connection.

------------------------------------------------------------------------------------------------------------------

### read

#### Request
```json
{
  "property": "wifiStatus",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "wifiStatus",
  "result": {
    "connected": true,
    "slot": 0,
    "signal": 0,
    "error": 0
  }
}
```

#### Result
- `connected` - the current status of the WiFi connection
- `slot` - the credentials slot currently connected, either primary, `0` or secondary, `1`
- `signal` - signal strength as a percentage from 0% to 100%
- `error` - the error code for failure to connect to the SSID

> **NOTE:** Reasons for the WiFi not connecting to the SSID are:
>
> 
>
> `0` - Unknown error
>
> `1` - Authorisation expired
>
> `2` - Authorisation leave
>
> `3` - Association expired
>
> `4` - Too many associations
>
> `5` - Not authorised
>
> `6` - Not associated
>
> `7` - Association leave
>
> `8` - Association not authorised
>
> `9` - Disassociated pwrcap bad
>
> `10` - Disassociated supchan bad
>
> `11` - IE invalid
>
> `12` - MIC failure
>
> `13` - 4-way handshake timeout
>
> `14` - Group key update timeout
>
> `15` - IE in 4 way differs
>
> `16` - Group cipher invalid
>
> `17` - Pairwise cipher invalid
>
> `18` - AKMP invalid
>
> `19` - Unsupported RSN IE version
>
> `20` - Invalid RSN IE cap
>
> `21` - 802.1x authorisation failed
>
> `22` - Cipher suite rejected
>
> `23` - Beacon timeout
>
> `24` - No access point found
>
> `25` - Authorisation failure
>
> `26` - Association failure
>
> `27` - Handshake timeout

------------------------------------------------------------------------------------------------------------------

### write

#### Request
```json
{
  "property": "wifiStatus",
  "operation": 1,
  "payload": {
    "restart": true
  }
}
```

#### Payload
- `restart` - to restart the WiFi connection, `true`

#### Response
```json
{
  "success": true,
  "property": "wifiStatus",
  "result": {
    "message": "string"
  }
}
```

#### Result
- `message` - `"Restarting the WiFi connection"`
