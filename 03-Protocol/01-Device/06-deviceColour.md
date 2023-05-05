---
title: deviceColour
---

## deviceColour {% deviceBadge device="pebl" /%} 
Read or change to the device's onboard LED, which accepts the RGB format

------------------------------------------------------------------------------------------------------------------

### read
Read the current colour of the onboard LED

#### Request
```json
{
  "property": "deviceColour",
  "operation": 0
}
```

#### Response
```json
{
  "success": true,
  "property": "deviceColour",
  "result": {
    "colour": [
      0,
      0,
      0
    ]
  }
}
```

#### Result
- `colour` - array of red, green and blue integer values, for example, purple would be `[255,0,255]`

------------------------------------------------------------------------------------------------------------------

### write
Change the colour of the built in LED of the device

#### Request
```json
{
  "property": "deviceColour",
  "operation": 1,
  "payload": {
    "colour": [
      0,
      0,
      0
    ],
    "reset": true
  }
}
```

#### Payload
- `colour` - array of red, green and blue integer values, between 0 and 255

or 

- `reset` - boolean to reset the LED back to system colours

#### Response
```json
{
  "success": true,
  "property": "deviceColour",
  "result": {
    "colour": [
      0,
      0,
      0
    ]
  }
}
```

#### Result
- `colour` - array of red, green, blue integer values, for example, yellow would be `[255,255,0]`