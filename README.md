# STM32F103C8T6 Breakout Board

# Contents

1. [What is it?](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#what-is-it)
   - [Compact version](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#compact-version)
   - [Protobard version](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#protoboard-version)
   - [STM32F103C8T6 specifications](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#stm32f103c8t6-specifications)
2. [How do I get it?](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#how-do-i-get-it)
   - [Ordering instructions](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#ordering-instructions)
   - [Pricing information](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#pricing-information)
   - [Why should I get this instead of just buying a "Blue Pill"?](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#why-should-i-get-this-instead-of-just-buying-a-blue-pill)
   - [Suggested configurations](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#suggested-configurations)
      - [Minimum](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#minimum)
      - [Standard, no HSE oscillator](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#standard-no-hse-oscillator)
      - [Standard, with HSE oscillator](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#standard-with-hse-oscillator)
      - [Full](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#full)
   - [Pin-compatible MCUs](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#pin-compatible-mcus)
   - [Developing for GigaDevice MCUs](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#developing-for-gigadevice-mcus)
3. [How does it work?](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#how-does-it-work)
   - [Schematic](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#schematic)
   - [Pinout](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#pinout)
   - [PCB Silkscreen Text](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#pcb-silkscreen-text)
4. [Notes on editing the design files](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#notes-on-editing-the-design-files)
5. [References](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#references)

# PCB images

# What is it?
A breakout board for the STM32F103C8T6 MCU which can be purchased, fully assembled, from JLC PCB (not including any through-hole components such as a USB connector). Although the STM32F103C8T6 is $5.61/unit on JLC PCB at the time of this writing (09 Feb 21), a plethora of pin-compatible MCUs exist (including from another manufacturer named GigaDevice) which allow this board to be purchased in quantities of 10 for the prices shown below. Anywhere from 14 to 125 MCUs, that I could find, are pin-compatible with this breakout board. See the section [Pin-compatible MCUs](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#pin-compatible-mcus) for additional details.

|MCU Manufacturer   |Part number             |Unit price, assembled (Qty: 10)|Core      |Clock |Flash|RAM  |Notes                            |
|-------------------|------------------------|-------------------------------|----------|------|-----|-----|---------------------------------|
|GigaDevice         |GD32E230C8T6<sup>1</sup>|$2.95                          |Cortex-M23|72 MHz|64 kB|8 kB |No USB; Minimum configuration    |
|ST Microelectronics|STM32F031C6TR           |$3.31                          |Cortex-M0 |48 MHz|32 kB|4 kB |No USB; Minimum configuration    |
|GigaDevice         |GD32F150C6T6<sup>1</sup>|$4.55<sup>2</sup>              |Cortex-M23|72 MHz|32 kB|6 kB |Standard, with HSE, configuration|
|ST Microelectronics|STM32F302C8             |$5.13<sup>2</sup>              |Cortex-M4 |72 MHz|64 kB|16 kB|Standard, with HSE, configuration|

The unit price also drops significantly for orders of more than 10.

|MCU Manufacturer   |Part number             |Unit price, Qty: 10|Unit price, Qty: 15|Unit price, Qty: 20|Unit price, Qty: 25|Unit price, Qty: 30|Unit price, Qty: 50<sup>3</sup>|
|-------------------|------------------------|-------------------|-------------------|-------------------|-------------------|-------------------|-------------------------------|
|GigaDevice         |GD32E230C8T6<sup>1</sup>|$2.95              |$2.35              |$2.07              |$1.89              |$1.78              |$1.63                          |
|ST Microelectronics|STM32F031C6TR           |$3.31              |$2.71              |$2.43              |$2.25              |$2.14              |$1.99                          |
|GigaDevice         |GD32F150C6T6<sup>1</sup>|$4.55<sup>2</sup>  |$3.81<sup>2</sup>  |$3.46<sup>2</sup>  |$3.26<sup>2</sup>  |$2.97<sup>2</sup>  |$2.77<sup>2</sup>              |
|ST Microelectronics|STM32F302C8             |$5.13<sup>2</sup>  |$4.39<sup>2</sup>  |$4.04<sup>2</sup>  |$3.84<sup>2</sup>  |$3.55<sup>2</sup>  |$3.35<sup>2</sup>              |

### Notes
1. See [Developing for GigaDevice MCUs](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#developing-for-gigadevice-mcus) for a few tips about how to write code for these devices.
2. Plus \~$1 for a USB connector
3. 50 pieces is the maximum quantity that can be ordered from JLC PCB SMT assembly

## Compact version
<img src="https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board_compact/blob/main/compact_top.png" height="900"> <img src="https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board_compact/blob/main/compact_bottom.png" height="900">

## Protoboard version
<img src="https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board_protoboard/blob/main/protoboard_top.png" width="800">
<img src="https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board_protoboard/blob/main/protoboard_bottom.png" width="800">

## STM32F103C8T6 specifications
|Processor    |Core Size|Speed |Connectivity                                   |Peripherals                                                 |I/O|Program memory|RAM  |Data converters|
|-------------|---------|------|-----------------------------------------------|------------------------------------------------------------|---|--------------|-----|---------------|
|ARM Cortex-M3|32-bit   |72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37 |64 kB         |20 kB|ADC: 10x 12-bit|

# How do I get it?

## Ordering instructions

1. Download or clone this repository.
2. Choose which board you'd like to have built. The "compact" version measures 0.85" x 2.25" and is meant to fit in a standard breadboard, giving you 1-2 rows on either side to connect components and/or jumper wires. The "protoboard" version is the exact same layout but includes a prototyping area that resembles a half-size breadboard; it measures 1.9" x 3.9".
3. Choose which components you want to include on your breakout board. If it's not one of the prepared arrangements below (Minimum; Standard, no HSE; Standard, with HSE; or Full), edit the bill of materials ("bom") to include only those components that you want. The easiest way to do this is probably to start with the "Everything" list and simply delete the rows of the components you don't want to include.
   - The STM32F103C8T6 is included in the bill of materials by default. As was mentioned above, this MCU was an outrageous $5.61/unit at the time of this writing. If you want to use a different, pin-compatible MCU (see [Pin-compatible MCUs](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#pin-compatible-mcus) below for a list), don't forget to edit the part number for U1 (the MCU) in the "bom" file. Alternatively, JLC PCB allows you to search for and use a different part after you've uploaded the bill of materials.
   - Double-check L1 and R2, which are used if you **don't** intend to use AVDD or VBAT (respectively). If you **do** intend to use AVDD and/or VBAT, make sure L1 (for AVDD) and/or R2 (for VBAT) are **not** populated.
4. Follow [these instructions for ordering an assembled PCB from JLCPCB or MakerFabs](https://github.com/nathancharlesjones/Embedded-for-Everyone/wiki/3.-Building-a-circuit-on-a-PCB-and-connecting-it-to-the-rest-of-the-embedded-device#ordering-an-assembled-pcb).
   - Each time I ordered this board I was asked by the engineers at JLC PCB if the polarities of my components were correct. I'm not sure what they are looking at that seems to indicate to them that they might be incorrect, but the components are, in fact, oriented correctly in the cpl file, as confirmed by assembling and testing the board myself.
   - The slot for the Debug Edge connector (J3) is right at the manufacturing limits for JLC PCB. They recommend that slots have a minimum size of 1.0mm but in conversations with their engineers they've told me that slots as small as 0.8mm are possible. The slot used is 0.83mm wide and JLC PCB has manufactured it like this twice with no issues. If a 1.0mm slot is preferable and/or required, there is another part in the ["Debug-Edge_AVX-connectors" Eagle library](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/tree/main/libraries) with a slot this size. All you'll need to do is edit the Eagle files to use this part instead of the current one and then re-generate the Gerbers.

## Pricing information

To estimate how much a specific configuration of this breakout board will cost, add the cost of the MCU at the quantity desired to the cost of the configuration used (Minimum; Standard, no HSE; Standard, with HSE; or Full; see [Suggested configurations](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#suggested-configurations) for additional details) at that same quantity. If the MCU being used is an "Extended" component on JLC PCB's website, then you'll also need to add $3.00 to the total order, or $0.30/board (for quantities of 10). For example, using the GigaDevice GD32E230C8T6 as mentioned in [What is it?](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board#what-is-it), the total cost per board for quantities of 10 is $2.95 because we added the cost for the Minimum configuration in quantities of 10 ($2.04) to the cost of the MCU in that same quantity ($0.61) and added in $3.00 total ($0.30/board) for the Extended component fee.

```
Cost per board = Configuration cost +       MCU cost +           Extended component fee
(Qty: 10)        Minimum:            $2.04  GD32E230C8T6: $0.61  $0.30 (if applicable)
                 Standard, no HSE:   $2.30  STM32F031C6:  $0.97
                 Standard, with HSE: $3.22  GD32F150C6T6: $1.03
                 Full:               $3.99  STM32F302C8:  $1.61
```

## Why should I get this instead of just buying a "Blue Pill"?

The simple fact is that if your only concern is unit price, then you shouldn't. Even in small batch quantities, this breakout baord can't quite compete with unit pricess of $2 or $1.50 on sites like AliExpress, TaoBao, and BangGood. However, it has been [well-documented that counterfeit electronic components are rampant](https://github.com/nathancharlesjones/Embedded-for-Everyone/wiki/3.-Building-a-circuit-on-a-PCB-and-connecting-it-to-the-rest-of-the-embedded-device#sourcing-parts-and-avoiding-counterfeits) and in my first (and only) order of "Blue Pills" from AliExpress I received a batch of counterfeit MCUs which refused to work with any ST product (STM32CubeIDE and ST-Link). They seem to function fine using other development tools, but being counterfeit devices it's possible they could fail in unexpected ways. Common sources of counterfeit devices are recycled parts sold as new (which may or may not be the same part as what they're being advertised as), parts that came off the official assembly line and then failed a QA/QC, or parts that came off the official assembly "after hours" or in an unofficial capacity. This means my counterfeits (and any MCU bought from an unauthorized distributor such as AliExpress, TaoBao, and BangGood) (1) may look and act like the MCU I think I'm purchasing but are, in fact, a different MCU or (2) may not meet the manufacturer's specifications or may fail in unexpected ways. Thus, I would only recommend individuals to buy from unauthorized distributors if at least one of the following is true:
- You are an experienced developer who can detect when an MCU has failed or is not meeting specification
- It is of little to no concern if the MCU fails, either during development or while in use
- It is okay if some of the MCUs you purchase must, effectively, be thrown out

Additionally, the fact that this breakout board is pin-compatible with so many other MCUs allows for a small level of customization not available with the stock "Blue Pills".

## Suggested configurations

### Minimum
- Cost: Amount shown below + the cost of the MCU

|Unit price, Qty: 10|Unit price, Qty: 15|Unit price, Qty: 20|Unit price, Qty: 25|Unit price, Qty: 30|Unit price, Qty: 50|
|-------------------|-------------------|-------------------|-------------------|-------------------|-------------------|
|$2.04              |$1.44              |$1.16              |$0.98              |$0.87              |$0.72              |

- The minimum components required for the MCU to operate plus a reset button, power LED, and user LED.
- Includes:
   - Power filtering capacitors (C2-C8)
   - Reset circuit (C9, S1)
   - Power LED (LED1, R7)
   - User LED (LED2, R8)
   - BOOT0 current-limiting resistor (R3)
- User must short the pads of (separately) R4, R2 and L1.
- Constraints:
   - Power supply voltage must be 2-3.6V (>=2.4V if ADC is used)
   - AVDD connected directly to VDD (no high-frequency noise filtration)
   - No battery back-up
   - BOOT0 fixed at logical "0"
   - No external oscillators (therefore, no USB)

### Standard, no HSE oscillator
- Cost: Amount shown below + the cost of the MCU

|Unit price, Qty: 10|Unit price, Qty: 15|Unit price, Qty: 20|Unit price, Qty: 25|Unit price, Qty: 30|Unit price, Qty: 50|
|-------------------|-------------------|-------------------|-------------------|-------------------|-------------------|
|$2.30              |$1.69              |$1.40              |$1.23              |$1.12              |$0.97              |

- The components most likely to be needed for a typical application (that doesn't need the high-speed external oscillator for USB, high-speed UART, accurate timing, etc).
- Includes:
   - Power regulator, power filtering capacitors, blocking diodes, ferrite bead (U2, C1-C8, D1, D2, L1)
   - Reset circuit (C9, S1)
   - Power LED (LED1, R7)
   - User LED (LED2, R8)
   - BOOT0/BOOT1 current-limiting resistors (R3/5)
   - Shorting resistor to connect VBAT and VDD (R2)
- MCU can be powered from VDD (2-3.6V; >=2.4V if ADC is used), VIN (4.8-15V), or from USB (J5)
- User doesn't have to short any pads together (accomplished with a 0 ohm resistor, R2)
- User must populate J6/7 with a pin header and jumper in order to select the proper BOOT0/BOOT1 configuration
- Constraints:
   - No battery back-up
   - No external oscillators (therefore, no USB)

### Standard, with HSE oscillator
- Cost: Amount shown below + the cost of the MCU + $1 for a USB mini-B connector (optional)

|Unit price, Qty: 10|Unit price, Qty: 15|Unit price, Qty: 20|Unit price, Qty: 25|Unit price, Qty: 30|Unit price, Qty: 50|
|-------------------|-------------------|-------------------|-------------------|-------------------|-------------------|
|$3.22              |$2.48              |$2.13              |$1.93              |$1.64              |$1.44              |

- The components most likely to be needed for a typical application (including a high-speed external oscillator for USB, high-speed UART, accurate timing, etc).
- Includes:
   - Power regulator, power filtering capacitors, blocking diodes, ferrite bead (U2, C1-C8, D1, D2, L1)
   - Reset circuit (C9, S1)
   - Power LED (LED1, R7)
   - User LED (LED2, R8)
   - BOOT0/BOOT1 current-limiting resistors (R3/5)
   - External oscillator (Q1, C10)
   - Pull-up resistor on USB_DP (R1)
   - Shorting resistor to connect VBAT and VDD (R2)
- MCU can be powered from VDD (2-3.6V; >=2.4V if ADC is used), VIN (4.8-15V), or from USB (J5)
- Includes 8 MHz oscillator
- User doesn't have to short any pads together (accomplished with a 0 ohm resistor, R2)
- User must populate J6/7 with a pin header and jumper in order to select the proper BOOT0/BOOT1 configuration
- Constraints:
   - No battery back-up

### Full
- Cost: Amount shown below + the cost of the MCU + $1 for a USB mini-B connector (optional)

|Unit price, Qty: 10|Unit price, Qty: 15|Unit price, Qty: 20|Unit price, Qty: 25|Unit price, Qty: 30|Unit price, Qty: 50|
|-------------------|-------------------|-------------------|-------------------|-------------------|-------------------|
|$3.99              |$3.14              |$2.74              |$2.50              |$2.07              |$1.82              |

- All parts are populated (except R2, R4, and R6, since this configuration uses VBAT and BOOT0/BOOT1), including the LSE oscillator
- Includes:
   - Power regulator, power filtering capacitors, blocking diodes, ferrite bead (U2, C1-C8, D1, D2, L1)
   - Reset circuit (C9, S1)
   - Power LED (LED1, R7)
   - User LED (LED2, R8)
   - BOOT0/BOOT1 current-limiting resistors (R3/5)
   - External oscillators (Q1/2, C10/11)
   - Pull-up resistor on USB_DP (R1)
- MCU can be powered from VDD (2-3.6V; >=2.4V if ADC is used), VIN (4.8-15V), or from USB (J5)
- Includes 8 MHz and 32.786 kHz oscillators
- User must populate J6/7 with a pin header and jumper in order to select the proper BOOT0/BOOT1 configuration
- User must connect battery (1.8-3.6V) to VBAT

## Pin-compatible MCUs

Depending on how you count, there are anywhere from 14 to 125 other MCUs that are pin-compatible with this breakout board. I made a [spreadsheet with all 125 possibly pin-compatible MCUs](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/Supporting-documentation/Pin-compatible-MCUs.xlsx) (also in [PDF format](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/Supporting-documentation/Pin-compatible-MCUs.pdf), for online viewing) and added some notes about how they differ from the STM32F103C8T6 and also their stock and pricing information on JLC PCB. A note about the three categories of "pin-compatibility" follows.

The first category of pin-compatible MCUs are those that STM32CubeMX lists as pin-compatible with the STM32F103C8T6 if it is using the USB and JTAG peripherals and both external oscillators. There are **13** MCUs in that list (14 if you include the STM32F103C8T6 itself), which you can view by opening the spreadsheet above and filtering for only those MCUs listed as "TRUE" in the column named "Pin-compatibility (1)".

This list from STM32CubeMX doesn't tell the full story, however, since it seems to me that all it does is try to match pin names to see if a part is pin-compatible. If pins have the same function but are named differently (e.g. "SYS_SWCLK" on the STM32F103C8T6 vs "SYS_JTCK_SWCLK" on the STM32F030CC), STM32CubeMX doesn't match them as pin-compatible.

The second category of pin-compatible MCUs are those that STM32CubeMX lists as pin-compatible with the STM32F103C8T6 if only the SWD peripheral is being used. There are **31** MCUs in that list (32 if you include the STM32F103C8T6 itself), which you can view by opening the spreadsheet above and filtering for only those MCUs listed as "TRUE" in the column named "Pin-compatibility (2)".

Interestingly, there were actually 3 MCUs on this list that I do not think are pin compatible with the STM32F103C8T6. The STM32F318C8, STM32F328C8, and STM32F358CC each require an external device to monitor power-on reset, which effectively toggles a pin to let the MCU know when the power supply is stable and it's okay to start up. The requirement for an external device which isn't included on this breakout board made those MCUs incompatible in my estimation.

The third category of pin-compatible MCUs are those whose pinouts indicate that they would work with this breakout board without requiring any external components or jumper wires. There are **124** MCUs in that list (125 if you include the STM32F103C8T6), including 18 from another manufacturer named GigaDevice, which you can view by opening the spreadsheet above and filtering for only those MCUs listed as "TRUE" in the column named "Pin-compatibility (3)". Only 74 of those MCUs are available on JLC PCB, though, and only 32 are in-stock as of the time of this writing (11 Feb 2021).

Keep in mind that for this last category I'm only looking at the respective pinouts to determine if an MCU is "pin compatible". I have not checked each of these parts and cannot guarantee that they will work with this board without modifications, with the exception of the STM32L151C8T6 and STM32F302CBT6 (I used those two on my first two batches of breakout boards, owing to the high cost of the STM32F103C8T6 at the time of my order, and I can confirm that they work). It is often the case that small, critical details can be hidden away in other pieces of documentation such as the hardware development guide or reference manual, so I would strongly recommend that you take my notes as merely a guide and that you take a much closer look at the datasheets and hardware development guides to determine for yourself if an MCU listed will actually work with this breakout board. The STM32CubeMX tool can be useful if you don't want to wade through a bunch of datasheets, but it might not tell the full story of which MCUs are or are not pin-compatible.

## Developing for GigaDevice MCUs

Although GigaDevice may be an unknown manufacturer for some, the documentation for these MCUs seems well-done. What's more, they are supported by the Segger J-Link debug adapters.

I found all of the information I needed by going to the [manufacturer's website](https://www.gigadevice.com/) and searching for the part number I was interested in. There I found data sheets, reference manuals, peripheral libraries, and demonstration code for each part.

# How does it work?

## Schematic
<img src="https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/Supporting-documentation/STM32F103C8T6-breakout-board_schematic.png" width="1000">

The schematic for this breakout board includes 7 modules or sections:
1. MCU
   - The MCU itself and the 0.1" pin headers to which the MCU pins are connected (U1 and J1/J2/J9).
2. Power & USB
   - Power: Power regulator, power filtering capacitors, diode protection, LED indicator, and shorting resistor/ferrite bead (U2, D1, D2, C1-C8, LED1, R7, L1/R2).
   - USB: USB connector and pull-up resistor on USB_DP (J5 and R1).
     - J5 is a through-hole mini-B USB connector sized to fit part #2172034-1 from TE. Additionally, the 5 pins labeled "USB breakout" match the pinouts of the [micro-B](https://www.adafruit.com/product/1833) and [mini-B](https://www.adafruit.com/product/1764) USB breakout boards from Adafruit (also available on [Digi-Key](https://www.digikey.com/en/products/filter/adapter-breakout-boards/643?WT.z_header=search_go&s=N4IgjCBcoLQBxVAYygMwIYBsDOBTANCAPZQDa4ArAEwIC6AvvYVWSAK7YBGABJwE650AayJsALiAZA)). You might want to use the USB breakout boards either if you strongly desired to use a micro-B USB cable with the breakout board or if you were disinterested in soldering the mini-B connector. Use extra-long headers on the STM32 breakout if you want to use the USB breakout boards and also still have those pins connected to your breadboard.
   - Only C2-C8 and L1 are technically required for MCU operation.
   - If U2 is used, D1 and D2 are strongly recommended, though not technically required. D1 and D2 allow for the MCU to be powered from both the VIN pin and USB connector (J5) at the same time without them damaging each other.
   - VDD/AVDD can serve as power inputs (if NEITHER VIN NOR USB (J5) are used) or as a power output (if EITHER VIN OR USB (J5) are used). Do NOT attempt to power the MCU from VDD if EITHER VIN OR USB (J5) are used; the output of the voltage regulator (U2) is tied directly to VDD and one power source may back-power the other if VIN/USB (J5) is powered at the same as VDD. The MCU is powered from USB by default whenever a USB cable is plugged in to J5 so you'll need to be careful about removing any external power sources connected to VDD if you're also using the USB peripheral on the MCU.
   - VDD is 2-3.6V (or 2.4-3.6V if the ADC is used).
   - VIN is 4.8-15V and goes through D2 to U2.
   - VBAT is 1.8-3.6V and provides a battery back-up for the MCU.
     - If you **DO** intend to use this feature, leave R2 open.
     - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R2 (or simply short the pads together) to connect VBAT to VDD.
     - For some of the pin-compatible MCUs (such as the STM32L151 MCU that I first tested this PCB with), "VBAT" becomes "VLCD", which controls the contrast of a connected LCD. See the appropriate datasheet/hardware development guide for further details.
   - AVDD is the power supply for the MCU's analog circuitry. For the STM32F103C8T6, AVDD should be at the same voltage as VDD. A ferrite bead, L1, connects the two together while providing some protection for AVDD from high-frequency noise on VDD.
     - For some of the pin-compatibe MCUs, AVDD is allowed to be a different voltage from VDD. If you use one of those MCUs and intend to use a different AVDD, then leave L1 open.
   - The graphic below depicts a simplified schematic of the power section for this breakout board. From this I hope it is clear what was stated above: that the MCU can be powered from any of the pins labeled "VD", "VN", and "VU", as well as from the USB connector, J5, and the pins "AV" and "BT" (assuming you're using neither the analog voltage nor the battery back-up and that L1 and R2 are both out-fitted) but it should NEVER be powered from more than one at a time. The only exception to this is that "VN" can be used at the same time as EITHER "VU" or J5 (but not both), since those two connections are the only two that are diode-protected. This allows the MCU to be powered by an external power source at the same time it is connected to a USB cable. The "VD", "AV", and "BT" pins may also be used as a power outputs if the system is being powered from another source (and, again, L1 and R2 have been out-fitted).
   <img src="https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/Supporting-documentation/STM32F103C8T6-breakout-board_power-section-graphic.png" width="1000">
3. Reset
   - The reset button and smoothing capacitor (S1 and C9).
4. BOOT0/BOOT1
   - Selection pin headers, current-limiting resistors, and pull-down resistors (J6/7, R3/5, and R4/6)
   - BOOT0/BOOT1 select which part of the MCU's memory is run at start-up (see [AN2586, Getting started with STM32F10xxx hardware development](https://www.st.com/resource/en/application_note/cd00164185-getting-started-with-stm32f10xxx-hardware-development-stmicroelectronics.pdf) for more details).
   - If you **DO** intend to use this feature, leave R4/6 open.
   - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R4 (or simply short the pads together) to pull BOOT0 to ground. R5/6 need not be populated, since the MCU only looks at BOOT1 if BOOT0 is a logical "1"; otherwise, the BOOT1 pin acts like a normal GPIO.
   - (R6 was included by virtue of mirroring the schematic for BOOT0, but it's probably not needed, unless someone wants the MCU to permanently boot from "System Memory".)
5. External oscillators
   - Crystal oscillators and power filtering capacitors (Q1/2 and C10/11)
   - An external crystal oscillator will have higher accuracy than the internal clock, which improves the accuracy of the internal timers and may be necessary for applications such as high-speed UART, USB, and RTC.
6. User LED
   - LED, current-limiting resistor, and option jumper (LED2, R8, and J8)
   - J8 is used to optionally remove the LED from the circuit, should you wish to not have the LED connected to its GPIO (as might be the case if you were using this GPIO for another purpose and needed to make sure you weren't exceeding the maximum current out on this pin).
   - To remove LED2 from the circuit, cut the trace between the terminals of J8 on the BOTTOM of the PCB (where its marked on the silkscreen).
   - To reinsert LED2, place a pin header and jumper in J8. The jumper now controls whether LED2 is included in the circuit or not.
7. Debug connectors (J3/J4 and the 4 pins labeled "ST-Link")
   - J4 is configured to match the pinout of the 10-pin connector on the J-Link Edu Mini.
   - J3 is intended for use with a series of board-to-board connectors by AVX, popularly called ["Debug Edge"](https://www.debug-edge.io). The purpose, once an [adapter board](https://github.com/nathancharlesjones/Debug-Edge_SWD-to-J-Link-Edu-Mini-adapter-with-USB-power) is acquired, is to save the developer from having to purchase J4 for development with the J-Link Edu Mini, which can save ~$0.50/board (not including tax and shipping). The adapter board mentioned previously also includes a USB connector for powering the MCU (connects directly to VDD and so should not be used when VIN or USB (J5) are also used).
   - The bottom four pins of J2 match the four pins on an ST-Link required to program this MCU. If you want to use these pins and still have them connected to a breadboard, I would recommend soldering extra-long male headers onto these pins (and normal male headers on the rest of J1/2).

## Pinout

The pin labels were limited to 2 characters, so I feel like they ended up being a bit cryptic. Below is a pinout for the breakout board with some additional information for the pins whose function isn't immediately clear.

|Port/Pin #|Name         |Label|                |Label|Name |Port/Pin #|
|----------|-------------|-----|----------------|-----|-----|----------|
|          |             |A4   |LEDs / Boot pins|A3   |     |          |
|          |             |A5   |                |AV   |AVDD |          |
|          |             |A6   |                |A2   |     |          |
|          |             |A7   |                |A1   |     |          |
|          |             |B0   |                |A0   |     |          |
|          |             |B1   |                |C13  |     |          |
|          |             |B2\* |                |BT   |VBAT |          |
|          |             |B10\*|                |B9\* |     |          |
|          |             |B11\*|                |B8\* |     |          |
|          |             |B12\*|                |B7\* |     |          |
|          |             |B13\*|                |B6\* |     |          |
|          |             |B14\*|                |B5   |     |          |
|          |             |B15\*|                |TR\* |JTRST|B4        |
|          |             |A8\* |                |DI\* |JTDI |A15       |
|          |             |A9\* |                |RS   |nRST |          |
|          |             |A10\*|                |SW\* |SWO  |B3        |
|          |VIN (4.8-15V)|VN   |                |IO\* |SWDIO|A13       |
|          |VUSB         |VU   |                |GD   |     |          |
|A11       |             |D-\* |                |CK\* |SWCLK|A14       |
|A12       |             |D+\* |                |VD   |VDD  |          |
|          |             |GD   |                |     |     |          |
|          |             |GD   |USB / Debug Edge|     |     |          |

### Notes
\* = 5V tolerant pin

## PCB Silkscreen Text
> - -------POWER-------
> - VDD/AVDD: 2-3.6V. Must be 3.3V if C39097/C387415 are used for Q1/Q2.
> - VUSB: 5V from USB (J5)
> - VIN: 4.8-15V
> - BAT: 1.8-3.6V. Short R2 if unused.
> - **WARNING**: Do NOT power MCU from VDD if EITHER VIN or USB (J5) are also being used.
> - --------GPIO--------
> - Max current, ea pin: 25 mA
> - Max current, total: 150 mA OUT (minus MCU power, ~7-50 mA) and 150 mA IN (minus MCU power)
> - \*=5V tolerant
> - USER LED (LED2) on PA3; Cut trace btwn J8 on BOTTOM of PCB to remove
> - --------BOM-------
> - All parts 0402 unless noted.
> - U1: STM32F103C8T6
> - U2: 2-3.6V regulator, >=150mA / SOT-223
> - J3: Debug Edge connector
> - J4: J-Link connector
> - J5: Mini-B; TE 2172034-1
> - Q1: 8MHz / 3.2x2.5mm
> - Q2: 32.768kHz / 3.2x2.5mm
> - L1: ferrite bead, 0805 (leave open for AVDD other MCU)
> - C3, C4, C5, C7-C11: 100nF
> - R1: 1k5     | C6: 1uF
> - C1, C2: 10uF
> - R3, R5: 10k | R8, R9: 150R
> - D1, D2: Shottky / SOD-123
> - LED1, LED2: 0603
> - R2, R4: 0R (use R4 in lieu of J6/J7)
> - S1: SPST-NO / 5.1x5.1mm
> - FMI: github.com/nathancharlesjones/STM32F103C8T6-breakout-board

# Notes on editing the design files

Both my original Eagle project files and a design block made from the project files are available (for both the compact and protoboard versions). You should be able to use either to edit the design.

You'll need to following libraries in order for the PCB to display correctly:
  - [SparkFun](https://github.com/sparkfun/SparkFun-Eagle-Libraries)
  - [Adafruit](https://github.com/adafruit/Adafruit-Eagle-Library)
  - [Seeed OPL](https://github.com/Seeed-Studio/OPL_Eagle_Library)
  - [USB connector](https://componentsearchengine.com/part-view/2172034-1/TE%20Connectivity)
  - [STM32F103C8T6](https://app.ultralibrarian.com/details/BD9A5901-10A2-11E9-AB3A-0A3560A4CCCC/STMicroelectronics/STM32F103C8T6?ref=digikey)
  - crystal-geyer_V1_0 (for the two oscillators; built-in Eagle library)
  - [Debug Edge connector](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/tree/main/libraries)

The only part of the layout which may be critical are the USB DP and DM traces. Based on [this appnote](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/References/AN4879_USB-hardware-and-PCB-guidelines-using-STM32-MCUs.pdf), it seems like they should be length-matched, which I was able to accomplish by adding a meander to DP (the squiggly part of the trace just above the USB connector). This doesn't include the short jog that each trace makes to the header pins on the left side of the PCB.

# References
- [STM32F103C8 product page](https://www.st.com/en/microcontrollers-microprocessors/stm32f103c8.html)
- [AN2586, Getting started with STM32F10xxx hardware development](https://www.st.com/resource/en/application_note/cd00164185-getting-started-with-stm32f10xxx-hardware-development-stmicroelectronics.pdf)
- [DS5319](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf), STM32F103C8 datasheet
- [RM0008](https://www.st.com/resource/en/reference_manual/cd00171190-stm32f101xx-stm32f102xx-stm32f103xx-stm32f105xx-and-stm32f107xx-advanced-armbased-32bit-mcus-stmicroelectronics.pdf), STM32F103 reference manual
