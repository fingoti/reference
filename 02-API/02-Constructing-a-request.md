---
title: Constructing a request
---


{% tabs %}


{% tab label="Command object" %}

# Command object

```json
{
    "response": true,
    "serial": "string",
    "key": "string",
    "request": []
}
```

This is the Command object for the `sendrequest` API endpoint {% infoHover %}Use an API client to POST to the URL <https://api.fingoti.com/v1/device/sendrequest>.{% /infoHover %}. This endpoint permits you to send requests to a Fingoti device, using pre-programmed device protocol commands - documented in [Reference &rarr; Protocol](https://documentation.fingoti.com/reference).

## Truth table

|          | Cloud   | Portal  | Local   | 
| -------- | ------- | ------- | ------- | 
| Response | &#9745; | &#9746; | &#9746; | 
| Serial   | &#9745; | &#9746; | &#9746; | 
| Key      | &#9746; | &#9746; | &#9745; | 
| Request  | &#9745; | &#9745; | &#9745; | 


{% tabs %}

{% tab label="Cloud" %}

```json
{
    "response": true,
    "serial": "string",
    "request": []
}
```

{% /tab %}

{% tab label="Portal" %}

```json
{
    "request": []
}
```

{% /tab %}

{% tab label="Local" %}

```json
{
    "key": "string",
    "request": []
}

```
{% /tab %}

{% /tabs %}


## Properties


{% tabs %}

{% tab label="Response" %}

`"response"` {% datatypeBadge %}Boolean{% /datatypeBadge %}

## Valid input

- `true`
- `false`

{% table %}

* Local
* Cloud
* Portal
---
*
    - Defaults to `true`: always sends a response
    - Ignores value provided by the user
*
    - When `false`: only confirms that the command has been sent
    - When `true`: waits for a reply
* 
    - Defaults to `true`: always sends a response
    - Used to provide error messages
    - Cannot be configured by the user

{% /table %}
    
{% /tab %}

{% tab label="Serial" %}
    
`"serial"` {% datatypeBadge %}String{% /datatypeBadge %}

## Valid input

```
A1B2C3D4E5
F6G7H8I9J0
F1N8O7I4O4
```

10-character string composed of a capital letter, followed by a digit between 1 and 9 - repeated five times.

Visible from [the Devices page](https://portal.fingoti.com/devices), or printed on the device.

{% table %}

* Local
* Cloud
* Portal
---
*
    - Not required
    - Ignores value provided by the user
*
    - Required
* 
    - Not required
    - Cannot be configured by the user

{% /table %}

{% /tab %}

{% tab label="Key" %}
    
`"key"` {% datatypeBadge %}String{% /datatypeBadge %}

## Valid input

Random 16-character string composed of numbers, lower and uppercase letters.

- Go to [the Devices page](https://portal.fingoti.com/devices)
- Press the Settings cog on the device you wish to use
- Press the Copy button (to the top-right &nearr; of the Key box)

{% table %}

* Local
* Cloud
* Portal
---
*
    - Required
*
    - n/a
    - Follow the steps in [Documentation &rarr; Account management &rarr; API key management &rarr; Authenticate with a Bearer token](https://documentation.fingoti.com/documentation)
* 
    - n/a
    - Follow the steps in [Documentation &rarr; Organisation management &rarr; API key management &rarr; Authenticate with a Bearer token](https://documentation.fingoti.com/documentation)

{% /table %}

{% /tab %}

{% tab label="Request" %}
    
`"request"` {% datatypeBadge %}Array{% /datatypeBadge %}

## Valid input

{% table %}

* Local
* Cloud
* Portal
---
*
    - Required
*
    - Required
* 
    - Required

{% /table %}

{% /tab %}

{% /tabs %}



{% /tab %}


{% tab label="Request object" %}

## Request object


{% tabs %}

{% tab label="Request" %}

```json
{
  "property": "string",
  "operation": 0
}

```
{% /tab %}

{% tab label="Command & Request" %}

```json
{
    "response": true,
    "serial": "string",
    "key": "string",
    "request": [
        {
            "property": "string",
            "operation": 0
        }
    ]
}
```

{% /tab %}

{% /tabs %}


The Request object {% infoHover %}The Request object is a child of the command object.{% /infoHover %} defines the device command to be sent, and whether the property is read or written to.

Device commands can be seen from [the Reference &rarr; Protocol page](https://developer.fingoti.com/hardware/protocol).

## Truth table

|          | Cloud   | Portal  | Local   | 
| -------- | ------- | ------- | ------- | 
| Response | &#9745; | &#9746; | &#9746; | 
| Serial   | &#9745; | &#9746; | &#9746; | 
| Key      | &#9746; | &#9746; | &#9745; | 
| Request  | &#9745; | &#9745; | &#9745; | 


{% tabs %}

{% tab label="Cloud" %}

```json
{
    "response": true,
    "serial": "string",
    "request": [
        {
            "property": "string",
            "operation": 0
        }
    ]
}
```

{% /tab %}

{% tab label="Portal" %}

```json
{
    "request": [
        {
            "property": "string",
            "operation": 0
        }
    ]
}
```

{% /tab %}

{% tab label="Local" %}

```json
{
    "key": "string",
    "request": [
        {
            "property": "string",
            "operation": 0
        }
    ]
}
```

{% /tab %}

{% /tabs %}



{% /tab %}


{% tab label="Payload object" %}

### Payload object

Payload objects are dependent on the device command sent. For example, `i2cData`.


{% tabs %}

{% tab label="Payload" %}

```json
{
    "payload": {
        "address": 3,
        "profile": [] 
    }
}
```

{% /tab %}

{% tab label="Request & Payload" %}

```json
{
    "property": "i2cData",
    "operation": 1,
    "payload": {
        "address": 3,
        "profile": []
    }
}
```

{% /tab %}

{% tab label="Command & Request & Payload" %}

```json
{
    "response": true,
    "serial": "string",
    "key": "string",
    "request": [
        {
            "property": "i2cData",
            "operation": 1,
            "payload": {
                "address": 3,
                "profile": []
            }
        }
    ]
}
```

{% /tab %}

{% /tabs %}


## Truth table

|          | Cloud   | Portal  | Local   | 
| -------- | ------- | ------- | ------- | 
| Response | &#9745; | &#9746; | &#9746; | 
| Serial   | &#9745; | &#9746; | &#9746; | 
| Key      | &#9746; | &#9746; | &#9745; | 
| Request  | &#9745; | &#9745; | &#9745; | 


{% tabs %}

{% tab label="Cloud" %}

```json
{
    "response": true,
    "serial": "string",
    "request": [
        {
            "property": "string",
            "operation": 1,
            "payload": {
                "address": 3,
                "profile": []
            }
        }
    ]
}
```

{% /tab %}

{% tab label="Portal" %}

```json
{
    "request": [
        {
            "property": "string",
            "operation": 1,
            "payload": {
                "address": 3,
                "profile": []
            }
        }
    ]
}
```

{% /tab %}

{% tab label="Local" %}

```json
{
    "key": "string",
    "request": [
        {
            "property": "string",
            "operation": 1,
            "payload": {
                "address": 3,
                "profile": []
            }
        }
    ]
}
```
{% /tab %}

{% /tabs %}


{% /tab %}


{% /tabs %}

