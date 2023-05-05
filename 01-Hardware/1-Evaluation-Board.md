---
title: Evaluation Board Developer Reference
---


This page provides an overview of the I2C devices present on the Fingoti Evaluation Board.

## Primer

### I2C device addressing

Device addresses are expressed as 8-bit. The leftmost bit is always `0`, as if it were 7-bit.

I2C device addresses are 7-bit, with the read/write bit excluded.

- Hexadecimal numbers are prefixed with `0x`
- Binary numbers are prefixed with `0b`
- Decimal numbers have no prefix

### Significant Bits

- The leftmost byte is referred to as the Most Significant Bit (MSB)

  The MSB comprises the decimal values between 256 and 65,535.

- The rightmost byte is referred to as the Least Significant Bit (LSB)

  The LSB comprises the decimal values between 1 and 255.

{% tabs %}

{% tab label="64K write-protectable EEPROM"%}

[View the datasheet](https://raw.githubusercontent.com/fingoti/reference/8882234d33e4dd2e2e614f406bea6f84e47a1b5b/assets/24CW16X-24CW32X-24CW64X-24CW128X-Data-Sheet-20005772B.pdf).

## Device address

| DEC  | HEX    | BIN            |
| ---- | ------ | -------------- |
| `80` | `0x50` | `0b 0101 0000` |

{% contextualCallout severity="info" %}
See Tables 3-1 and 3-2, on pages 8-9 in the datasheet.
{% /contextualCallout %}

> The 7-bit slave address is constructed using two groups of bits. The first four bits contain the Device Type Identifier, followed by three bits containing the hardware slave address bits.
>
> …
>
> The 3-bit hardware slave address is comprised of bits A2, A1 and A0.

![Screenshot of the Table of Valid Device Address Bytes](assets/valid-device-address.png)

![Screenshot of the Device Preset Slave Address table](assets/device-preset-address.png)

The device type identifier is always `0b 1010`. As the part number {% infoHover %}`24CW640`{% /infoHover %} ends in `0`, the target address is `0b 000`.

## Write operations

{% contextualCallout severity="info" %}
See Figures 6-1 and 6-2, on pages 12-13 in the datasheet.
{% /contextualCallout %}

| `2^14`  | `2^13` | `2^12` | `2^11` | `2^10` | `2^9` | `2^8` | `2^7` | `2^6` | `2^5` | `2^4` | `2^3` | `2^2` | `2^1` | `2^0` |
| ------- | ------ | ------ | ------ | ------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| `16384` | `8192` | `4096` | `2048` | `1024` | `512` | `256` | `128` | `64`  | `32`  | `16`  | `8`   | `4`   | `2`   | `1`   |

On 64-Kbit chips {% infoHover %}Referred to as `24CW64X` in the datasheet.{% /infoHover %}, `A13` is an impartial {% infoHover %}Referred to as 'don't care bit' in the datasheet.{% /infoHover %} bit.

There are only 8,192 bytes available in total, which is equal to `2^13`. Only the 128-Kbit chip can use `A13`, as it has 16,384 bytes, which is equal to `2^14`.

### Byte write

![Screenshot of the Byte Write figure](assets/byte-write.png)

```json
["S", "W0", "W1", "W100", "P"]
```

Writes `100` to the following word address:

| DEC | HEX    | BIN            |
| --- | ------ | -------------- |
| `1` | `0x01` | `0b 0000 0001` |

- Set the word address (cursor position) at a given byte

  Start writing from the cursor position.

- Write the byte

### Page write

![Screenshot of the Page Write figure](assets/page-write.png)

```json
[
  "S",
  "W0",
  "W1",
  "W104",
  "W101",
  "W108",
  "W108",
  "W111",
  "W32",
  "W119",
  "W111",
  "W114",
  "W108",
  "W100",
  "P"
]
```

Writes `hello world` {% infoHover %}Text is converted to binary via ASCII codes.{% /infoHover %} (using a partial page write) to the following word address:

| DEC | HEX    | BIN            |
| --- | ------ | -------------- |
| `1` | `0x01` | `0b 0000 0001` |

- Set the word address (cursor position) at a given byte

  Start writing from the cursor position.

- Write up to 32 bytes

## Read operations

{% contextualCallout severity="info" %}
See Figures 7-1, 7-2, and 7-3, on pages 17-19 of the datasheet.
{% /contextualCallout %}

### Current address read

![Screenshot of the Page Write figure](assets/current-address-read.png)

```json
["S", "R1", "P"]
```

Reads the next byte, according to the internal Address Pointer, which 'maintains the word address of the last byte accessed, internally incremented by one'.

{% contextualCallout severity="warning" %}
This operation produces unreliable results. Use random read for a single byte, or sequential read for many bytes.
{% /contextualCallout %}

### Random read

![Screenshot of the Page Write figure](assets/random-read.png)

```json
["S", "W0", "W3", "S", "R1", "P"]
```

Reads a single byte, starting from the word address:

| DEC | HEX    | BIN            |
| --- | ------ | -------------- |
| `3` | `0x03` | `0b 0000 0011` |

- Set the word address (cursor position) at a given byte

  Start reading from the cursor position.

- Flip the read/write bit by repeating a start condition

- Read a single byte

### Sequential read

![Screenshot of the Page Write figure](assets/sequential-read.png)

```json
["S", "W0", "W1", "S", "R11", "P"]
```

Reads eleven bytes {% infoHover %}Specifically, the `hello world` written earlier.{% /infoHover %}, starting from the word address:

| DEC | HEX    | BIN            |
| --- | ------ | -------------- |
| `1` | `0x01` | `0b 0000 0001` |

- Set the word address (cursor position) at a given byte

  Start reading from the cursor position.

- Flip the read/write bit by repeating a start condition

- Read up to 32 bytes

{% /tab %}

{% tab label="Temperature and humidity sensor"%}

[View the datasheet](https://raw.githubusercontent.com/fingoti/reference/8882234d33e4dd2e2e614f406bea6f84e47a1b5b/assets/Sensirion_Humidity_SHT3x_Datasheet_digital-767294.pdf).

## Documented features

- [x] Single shot data acquisition mode
- [x] Periodic data acquisition mode
- [ ] ART
- [ ] Break
- [ ] Reset
- [ ] Heater

## Maximum delays by repeatability

{% contextualCallout severity="info" %}
Repeatability influences how reproducible readings will be, by stipulating how long measurements are taken for.

Repeatability also affects current consumption and noise level. See Sections 2.1 and 2.2, on page 5 of the datasheet.
{% /contextualCallout %}

| Low | Medium | High |
| --- | --- | --- |
| `D4` | `D6` | `D15`

{% contextualCallout severity="info" %}
See Section 2.2, Table 4, on page 5 of the datasheet.
{% /contextualCallout %}

## Device address

| DEC | HEX | BIN |
| --- | --- | --- |
| `68` | `0x44` | `0b 0100 0100` |

{% contextualCallout severity="info" %}
See Section 3.4, Table 7, on pages 7-8 in the datasheet.

If you are not using the Portal, see Section 4.2, page 9.
{% /contextualCallout %}

## Single shot data acquisition mode

Measure and fetch commands *must* be combined in single shot mode (unlike periodic mode, where it is purely a convenience).

The maximum delay for the given repeatability ([see above](#maximum-delays-by-repeatability)) must be provided before the repeated Start condition.

### Measuring

{% contextualCallout severity="info" %}
See Section 4.3, Table 8, on pages 9-10 in the datasheet.
{% /contextualCallout %}


#### Clock stretching (MSB)

| Enabled | Disabled |
| --- | --- |
| `W44` | `W36` |

#### Repeatability (LSB)

| Clock stretching | Low | Medium | High |
| --- | --- | --- | --- |
| Enabled | `W16` | `W13` | `W6` |
| Disabled | `W22` | `W11` | `W0` |

#### Commands

{% tabs %}

{% tab label="Clock stretching enabled" %}
From low to high repeatability.

```json
["S", "W44", "W16", "P"]
["S", "W44", "W13", "P"]
["S", "W44", "W6", "P"]
```
{% /tab %}

{% tab label="Clock stretching disabled" %}
From low to high repeatability.

```json
["S", "W36", "W22", "P"]
["S", "W36", "W11", "P"]
["S", "W36", "W0", "P"]
```
{% /tab %}

{% /tabs %}

### Fetching

{% contextualCallout severity="info" %}
See Section 4.4, on page 10 of the datasheet.
{% /contextualCallout %}

#### Commands

{% tabs %}

{% tab label="Temperature, humidity, and checksums" %}
Reads six bytes of temperature and humidity data, including both checksums.

```json
["S", "R6", "P"]
```
{% /tab %}

{% tab label="Temperature and humidity only" %}
Reads five bytes of temperature and humidity data, excluding the humidity checksum.

```json
["S", "R5", "P"]
```
{% /tab %}

{% tab label="Temperature only" %}
Reads two bytes of temperature data.

```json
["S", "R2", "P"]
```
{% /tab %}

{% /tabs %}

### Measure and fetch

{% contextualCallout severity="warning" %}
Only use commands with clock stretching disabled.

Single shot commands with clock stretching *enabled* will cause all three I2C devices on the Evaluation Board to stop responding. This is corrected by pressing the Reset button on the Board.
{% /contextualCallout %}

{% tabs %}

{% tab label="Clock stretching enabled" %}
From low to high repeatability.

```json
["S", "W44", "W16", "D4", "S", "R6", "P"]
["S", "W44", "W13", "D6", "S", "R6", "P"]
["S", "W44", "W6", "D15", "S", "R6", "P"]
```
{% /tab %}

{% tab label="Clock stretching disabled" %}
From low to high repeatability.

```json

["S", "W36", "W22", "D4", "S", "R6", "P"]
["S", "W36", "W11", "D6", "S", "R6", "P"]
["S", "W36", "W0", "D15", "S", "R6", "P"]
```
{% /tab %}

{% /tabs %}

## Periodic data acquisition mode

Measure and fetch commands can be performed separately.

For example, a measure command is sent once to "initialise" the sensor:

{% callout %}
This command takes a measurement once every two seconds, with high repeatability.
{% /callout %}

```json
["S","W34","W43","P"]
```

Then, fetch commands are sent:

{% callout %}
Fetch commands always begin by setting the MSB to `0xE0`.
{% /callout %}

```json
["S","W224","W0","S","R6","P"]
```


However, if the Evaluation Board loses power, the sensor will "forget" the measurement command. Thus, it may be more pertinent to send "Measure and fetch" commands at all times.

### Measuring

{% contextualCallout severity="info" %}
See Section 4.5, Table 9, on page 11 of the datasheet.
{% /contextualCallout %}

Measurement commands are differentiated by data acquisition frequency (mps) {% infoHover %}Set in the MSB.{% /infoHover %} and repeatability {% infoHover %}Set in the LSB.{% /infoHover %}.

> The data acquisition frequency and the repeatability setting influences the measurement duration and the current consumption of the sensor. This is explained in section 2.2 ...

#### Measurements per second (MSB)

| mps | Command |
| --- | ------- |
| 0.5 | `W32`   |
| 1   | `W33`   |
| 2   | `W34`   |
| 4   | `W35`   |
| 10  | `W39`   |

#### Repeatability (LSB)

| mps | Low   | Medium | High  |
| --- | ----- | ------ | ----- |
| 0.5 | `W50` | `W36`  | `W47` |
| 1   | `W48` | `W38`  | `W45` |
| 2   | `W54` | `W32`  | `W43` |
| 4   | `W52` | `W34`  | `W41` |
| 10  | `W55` | `W33`  | `W42` |

#### Commands

{% contextualCallout severity="info" %}
Fingoti devices can poll as often as once every single second, ergo taking one measurement every half-second (or one second) is impractical.
{% /contextualCallout %}

{% tabs %}

{% tab label="Once every two seconds" %}
From low to high repeatability.

```json
["S","W34","W54","P"]
["S","W34","W32","P"]
["S","W34","W43","P"]
```
{% /tab %}

{% tab label="Once every four seconds" %}
From low to high repeatability.

```json
["S","W35","W52","P"]
["S","W35","W34","P"]
["S","W35","W41","P"]
```
{% /tab %}

{% tab label="Once every ten seconds" %}
From low to high repeatability.

```json
["S","W39","W55","P"]
["S","W39","W33","P"]
["S","W39","W42","P"]
```
{% /tab %}

{% /tabs %}

### Fetching

{% contextualCallout severity="info" %}
See Section 4.6, Table 10, on page 11 of the datasheet.
{% /contextualCallout %}


{% contextualCallout severity="info" %}
When changing between a Write and Read command, you must add another Start condition.
{% /contextualCallout %}

#### Commands


{% callout %}
`W0` can be omitted from the command.
{% /callout %}

{% tabs %}

{% tab label="Temperature, humidity, and checksums" %}
Reads six bytes of temperature and humidity data, including both checksums.

```json
["S","W224","W0","S","R6","P"]
```
{% /tab %}

{% tab label="Temperature and humidity only" %}
Reads five bytes of temperature and humidity data, excluding the humidity checksum.

```json
["S","W224","W0","S","R5","P"]
```
{% /tab %}

{% tab label="Temperature only" %}
Reads two bytes of temperature data.

```json
["S","W224","W0","S","R2","P"]
```
{% /tab %}

{% /tabs %}

### Measure and fetch

{% contextualCallout severity="info" %}
The fetch command is always the same, the only difference is the number of bytes being read.
{% /contextualCallout %}

To fit your use case, change the number of bytes which are read.

{% tab label="Once every two seconds" %}
From low to high repeatability.

```json
["S","W34","W54","S","W224","W0","S","R6","P"]
["S","W34","W32","S","W224","W0","S","R6","P"]
["S","W34","W43","S","W224","W0","S","R6","P"]
```
{% /tab %}

{% tab label="Once every four seconds" %}
From low to high repeatability.

```json
["S","W35","W52","S","W224","W0","S","R6","P"]
["S","W35","W34","S","W224","W0","S","R6","P"]
["S","W35","W41","S","W224","W0","S","R6","P"]
```
{% /tab %}

{% tab label="Once every ten seconds" %}
From low to high repeatability.

```json
["S","W39","W55","S","W224","W0","S","R6","P"]
["S","W39","W33","S","W224","W0","S","R6","P"]
["S","W39","W42","S","W224","W0","S","R6","P"]
```
{% /tab %}

{% /tab %}

{% tab label="Ambient light sensor" %}

[View the datasheet](https://raw.githubusercontent.com/fingoti/reference/8882234d33e4dd2e2e614f406bea6f84e47a1b5b/assets/veml7700.pdf).

## Documented features

- [x] Configuration register
- [ ] High threshold windows
- [ ] Low threshold windows
- [ ] Power saving mode
- [x] High resolution output data
- [ ] White channel output data
- [ ] Interrupt status

## Device address

| DEC  | HEX    | BIN            |
| ---- | ------ | -------------- |
| `16` | `0x10` | `0b 0001 0000` |

## Configuration register

![The configuration register table](assets/configuration-register.png)

The ambient light sensor must be configured before use. As an example, the following command will set:

- Gain selection to 1
- Integration time setting to 100ms
- Persistence protect number setting to 1
- Interrupt enable setting to disabled
- Shut down setting to power on

{% contextualCallout severity="info" %}
The command code is written first, followed by the LSB, terminating with the MSB.
{% /contextualCallout %}

```json
["S", "W0", "W0", "W0", "P"]
```

The following command sets:

- Gain selection to 1/4
- Integration time setting to 800ms
- Persistence protect number setting to 8
- Interrupt enable setting to enabled
- Shut down setting to shut down

Bits that can be written are noted with the `^` character.

```
0b 0001 1000
      ^ ^ ^^
0b 1110 0011
   ^^^    ^^
```

```json
["S", "W0", "W243", "W24", "P"]
```

For more information, refer to the datasheet.

## High resolution output data (reading)

Once configured, read two bytes of high resolution output data.

```json
["S", "W4", "S", "R2", "P"]
```

{% /tab %}

{% /tabs %}