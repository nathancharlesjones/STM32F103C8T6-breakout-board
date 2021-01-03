# STM32F103C8T6 Breakout Board
![](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/master/STM32F103C8T6_PCB.png)

# How to order
1. Download or clone this repository.
2. Choose which board you'd like to have built. The "compact" version measures 0.85" x 2.25" and is meant to fit in a standard breadboard, giving you 1-2 wells on either side to connect components and/or jumper wires. The "protoboard" version is the exact same layout but includes a prototyping area that resembles a half-size breadboard; it measures 1.9" x 3.9".
3. Choose which components you want to include on your breakout board. If it's not one of the prepared arrangements below (Minimum, Standard, or Full), edit the bill of materials ("bom") to include only those components that you want. The easiest way to do this is probably to start with the "Everything" list and simply delete the rows of the components you don't want to include.
4. Follow [these instructions for ordering an assembled PCB from JLCPCB or MakerFabs](https://github.com/nathancharlesjones/Embedded-for-Everyone/wiki/3.-Building-a-circuit-on-a-PCB-and-connecting-it-to-the-rest-of-the-embedded-device#ordering-an-assembled-pcb).

# STM32F103C8T6 specifications
|Processor|Core Size|Speed|Connectivity|Peripherals|I/O|Program memory size|RAM size|Data converters|
|---|---|---|---|---|---|---|---|---|
|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|64 kB|20 kB|ADC: 10x 12-bit|

Unfortunately, at the time of this writing (02 Jan 2021), the STM32F103C8T6 is an outrageous $6.16/unit on JLC PCB. The following MCUs seem to be the next best alternatives, to me (see the section below for some additional information):
- STM32F302C8Tx
  - Cost on JLC PCB as of 02 Jan 2021: $2.12/unit (plus a $3.00 flat fee per order for it being an extended part)
  - None in stock
  - Notable differences between it and the STM32F103:
    - Cortex-M4 instead of Cortex-M3
    - Includes I2S
    - 16 kB RAM instead of 20 kB
    - 1 12-bit ADC instead of 10
    - 2 12-bit DACs instead of 0
- STM32F302CBTx
  - Cost on JLC PCB as of 02 Jan 2021: $2.87/unit (plus a $3.00 flat fee per order for it being an extended part)
  - Notable differences between it and the STM32F103:
    - Cortex-M4 instead of Cortex-M3
    - Includes I2S
    - 128 kB Flash instead of 64 kB
    - 32 kB RAM instead of 20 kB
    - 9 12-bit ADC instead of 10
    - 1 12-bit DACs instead of 0
- STM32F303CCTx
  - Cost on JLC PCB as of 02 Jan 2021: $2.28/unit (plus a $3.00 flat fee per order for it being an extended part)
  - Only 1 in stock
  - Notable differences between it and the STM32F103:
    - Cortex-M4 instead of Cortex-M3
    - Includes I2S
    - 256 kB Flash instead of 64 kB
    - 40 kB RAM instead of 20 kB
    - 15 12-bit ADC instead of 10
    - 2 12-bit DACs instead of 0
- STM32L151C8Tx
  - Cost on JLC PCB as of 02 Jan 2021: $1.95/unit
  - Notable differences between it and the STM32F103:
    - Max clock speed 32 MHz instead of 72 MHz
    - No CANbus
    - Includes I2S
    - 10 kB RAM instead of 20 kB
    - 4 kB EEPROM instead of 0 kB
    - 16 12-bit ADC instead of 10
    - 2 12-bit DACs instead of 0

|Part|Cost<sup>1</sup>|Stock o JLC PCB<sup>1</sup>|Core|Max clock|Flash|RAM|EEPROM|ADC (12b)|DAC (12b)|
|STM32F103C8T6|$6.16|7162|M3|72 MHz|64 kB|20 kB|N/A|10|0|
|STM32F302C8T6|$2.12<sup>2</sup>|0|M4|72 MHz|64 kB|16 kB|N/A|1|1|
|STM32F302CBT6|$2.87<sup>2</sup>|794|M4|72 MHz|128 kB|32 kB|N/A|9|1|
|STM32F303CCT6|$2.28<sup>2</sup>|1|M4|72 MHz|256 kB|40 kB|N/A|15|2|
|STM32L151C8T6|$1.95|798|M3|32 MHz|64 kB|10 kB|4 kB|16|2|

### Notes
1. As of 03 Jan 2021
2. Plus a $3.00 flat fee per order for this being an extended part

# Pin-compatible MCUs

**WARNING**: I have not checked each of these parts and cannot guarantee that they will work with this board without modifications. They are listed here merely to bring to the reader's attention that there _may_ be pin-compatible STM32 MCUs which _could_ work with this board in the event that the STM32F103C8T6 is not exactly the MCU they would like to use. If you are interested in using one of these other MCUs, I would recommend that you find the appropriate datasheet and hardware development guide from ST Microelectronics to ensure that this board will meet the requirements of any new MCU.

Using the STM32CubeMX tool, it appears to me that, as of this writing (02 Jan 2021), this board is exactly pin-compatible with the 13 MCUs below (the STM32F103C8Tx is shown in the first row for comparison).

|Part No.|Processor|Core Size|Speed|Connectivity|Peripherals|I/O|Program memory size|RAM size|Data converters|
|---|---|---|---|---|---|---|---|---|---|
|STM32F103C8Tx|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|64 kB|20 kB|ADC: 10x 12-bit|
|STM32F102C4Tx|ARM Cortex-M3|32-bit|48 MHz|I2C, SPI, UART/USART, USB, IrDA, LINbus|DMA, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|64 kB|4 kB|ADC: 10x 12b|
|STM32F102C6Tx|ARM Cortex-M3|32-bit|48 MHz|I2C, SPI, UART/USART, USB, IrDA, LINbus|DMA, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|32 kB|6 kB|ADC: 10x 12b|
|STM32F102C8Tx|ARM Cortex-M3|32-bit|48 MHz|I2C, SPI, UART/USART, USB, IrDA, LINbus|DMA, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|64 kB|10 kB|ADC: 10x 12b|
|STM32F102CBTx|ARM Cortex-M3|32-bit|48 MHz|I2C, SPI, UART/USART, USB, IrDA, LINbus|DMA, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|128 kB|16 kB|ADC: 10x 12b|
|STM32F103C4Tx|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|26|16 kB|6 kB|ADC: 10x 12b|
|STM32F103C6Tx|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|32 kB|10 kB|ADC: 10x 12b|
|STM32F103CBTx|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|128 kB|20 kB|ADC: 10x 12b|
|STM32F302C6Tx|ARM Cortex-M4|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, I2S, POR, PWM, WDT|37|32 kB|16 kB|ADC: 11x 12b; DAC: 1x12b|
|STM32F302C8Tx|ARM Cortex-M4|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, I2S, POR, PWM, WDT|37|64 kB|16 kB|ADC: 1x 12b; DAC: 1x12b|
|STM32F302CBTx|ARM Cortex-M4|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, I2S, POR, PWM, WDT|37|128 kB|32 kB|ADC: 9x 12b; DAC: 1x12b|
|STM32F302CCTx|ARM Cortex-M4|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, I2S, POR, PWM, WDT|37|256 kB|40 kB|ADC: 9x 12b; DAC: 1x12b|
|STM32F303CBTx|ARM Cortex-M4|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, I2S, POR, PWM, WDT|37|128 kB|32 kB|ADC: 15x 12b; DAC: 2x12b|
|STM32F303CCTx|ARM Cortex-M4|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, I2S, POR, PWM, WDT|37|256 kB|40 kB|ADC: 15x 12b; DAC: 2x12b|

If only the SWD pins are needed (meaning we are not using the external oscillators, JTAG pins, or USB) then the 18 MCUs below are also pin compatible with this breakout board (31 total). To avoid making a long article longer, I'll refrain from enumerating every possibility therein. I would encourage you to use the STM32 pin compatibility tool to find which of these MCUs may work with this development board for your own project (don't forget, initially, to UNselect "Ignore pinning status", "Ignore power pins", and "Ignore system pins" and then click "Search" in order to make sure that you're looking at a list of MCUs which have a very high likelihood of working with this development board).
- STM32F100C4Tx
- STM32F100C6Tx
- STM32F100C8Tx
- STM32F100CBTx
- STM32F101C4Tx
- STM32F101C6Tx
- STM32F101C8Tx
- STM32F101CBTx
- STM32F301C6Tx
- STM32F301C8Tx
- STM32F303C6Tx
- STM32F303C8Tx
- STM32F334C4Tx
- STM32F334C6Tx
- STM32F334C8Tx
- STM32F318C8Tx
- STM32F328C8Tx
- STM32F358CCTx


Things get even more interesting, however, if we DO select "Ignore power pins". With this selected (and having set "Debug" under "SYS" to "Trace Asynchronous Sw" instead of "JTAG (5 pin)"), we discover that 17 MCUs more than our inital list (30 total) appear to be pin compatible.
- STM32F373C8Tx
- STM32F373CBTx
- STM32F373CCTx
- STM32L151C6Tx
- STM32L151C8Tx
- STM32L151CBTx
- STM32L151C6TxA
- STM32L151C8TxA
- STM32L151CBTxA
- STM32L151CCTx
- STM32L152C6Tx
- STM32L152C8Tx
- STM32L152CBTx
- STM32L152C6TxA
- STM32L152C8TxA
- STM32L152CBTxA
- STM32L152CCTx

To determine if these truly are pin compatible, however, we would need to dive into the datasheets and/or hardware development guides to see where their power pins are and what their requirements are and if our board meets those requirements. For the L151, it appears that the only difference is that pin 1 is "VLCD" instead of "VBAT" and although the function changes, the hardware requirements are roughly the same (an external voltage may or may not be applied to this pin for various purposes and filtering capacitors are either required or recommended). In fact, this MCU was much cheaper on JLC PCB than the STM32F103C8T6 so the L151 is what I chose to populate the breakout board on my first order.


# Schematic
![](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/Supporting-documentation/STM32F103C8T6-breakout-board_schematic.png)

The schematic for this breakout board includes 7 modules or sections:
1. MCU
   - The MCU itself and the 0.1" pin headers to which the MCU pins are connected (U1 and J1/J2).
2. Power & USB
   - Power: Power regulator, power filtering capacitors, diode protection, LED indicator, and shorting resistor/ferrite bead (U2, D1, D2, C1-C8, LED1, R7, L1/R2).
   - USB: USB connector and pull-up resistor on USB_DP (USB1 and R1).
   - Only C2-C8 and L1 are technically required for MCU operation.
   - If U2 is used, D1 and D2 are strongly recommended, though not technically required. D1 and D2 allow for the MCU to be powered from both the VIN pin and USB1 connector at the same time without them damaging each other.
   - VDD/AVDD can serve as power inputs (if NEITHER VIN NOR USB1 are used) or as a power output (if EITHER VIN OR USB1 are used). Do NOT attempt to power the MCU from VDD if EITHER VIN OR USB1 are used; the output of the voltage regulator (U2) is tied directly to VDD and one power source may back-power the other if VIN/USB1 is powered at the same as VDD.
   - VDD is 2-3.6V (or 2.4-3.6V if the ADC is used).
   - VIN is 4.8-15V and goes through D2 to U2.
   - VBAT is 1.8-3.6V and provides a battery back-up for the MCU.
     - If you **DO** intend to use this feature, leave R2 open.
     - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R2 (or simply short the pads together) to connect VBAT to VDD.
     - For some of the pin-compatible MCUs (such as the STM32L151 MCU that I first tested this PCB with), "VBAT" becomes "VLCD", which controls the contrast of a connected LCD. See the appropriate datasheet/hardware development guide for further details.
   - AVDD is the power supply for the MCU's analog circuitry. For the STM32F103C8T6, AVDD should be at the same voltage as VDD. A ferrite bead, L1, connects the two together while providing some protection for AVDD from high-frequency noise on VDD.
     - For some of the pin-compatibe MCUs, AVDD is allowed to be a different voltage from VDD. If you use one of those MCUs and intend to use a different AVDD, then leave L1 open.
3. Reset
   - The reset button and smoothing capacitor (S1 and C9).
4. BOOT0/BOOT1
   - Selection pin headers, current-limiting resistors, and pull-down resistors (J6/7, R3/5, and R4/6)
   - BOOT0/BOOT1 select which part of the MCU's memory is run at start-up (see [AN2586, Getting started with STM32F10xxx hardware development](https://www.st.com/resource/en/application_note/cd00164185-getting-started-with-stm32f10xxx-hardware-development-stmicroelectronics.pdf) for more details).
   - If you **DO** intend to use this feature, leave R4/6 open.
   - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R4 (or simply short the pads together) to pull BOOT0 to ground. R5/6 need not be populated, since the MCU only looks at BOOT1 if BOOT0 is a logical "1"; otherwise, the BOOT1 pin acts like a normal GPIO.
5. External oscillators
   - Crystal oscillators and power capacitors (Q1/2 and C10/11)
   - An external crystal oscillator will have higher accuracy than the internal clock, which improves the accuracy of the internal timers and may be necessary for applications such as high-speed UART, USB, and RTC.
6. User LED
   - LED, current-limiting resistor, and option jumper (LED2, R8, and J8)
   - J8 is used to optionally remove the LED from the circuit, should you wish to not have the LED connected to its GPIO.
   - To remove LED2 from the circuit, cut the trace between the terminals of J8 on BOTTOM of the PCB (where its marked on the silkscreen).
   - To reinsert LED2, place a pin header and jumper in J8. The jumper now controls whether LED2 is included in the circuit or not.
7. J-Link and Debug Edge connectors (J3/4)
   - J4 is configured to match the pinout of the 10-pin connector on the J-Link Edu Mini.
   - J3 is intended for use with a series of board-to-board connectors by AVX, popularly called ["Debug Edge"](www.debug-edge.io). The purpose, once an [adapter board](https://github.com/nathancharlesjones/Debug-Edge_SWD-to-J-Link-Edu-Mini-adapter-with-USB-power) is acquired, is to save the developer from having to purchase J4 for development with the J-Link Edu Mini. The adapter board mentioned previously also includes a USB connector for powering the MCU (connects directly to VDD and so should not be used when VIN or USB1 are also used).

## Minimum components
- Cost: Approximately $8.19 per board on JLCPCB (in quantities of 10)
  - $3.98 per board to use the STM32L151C8T6 instead of the STM32F103
  - $5.20 per board to use the STM32F302CBT6 instead of the STM32F103
- The minimum components required for the MCU to operate plus a reset button, power LED, and user LED.
- Includes:
   - STM32F103C8T6 (U1)
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
   - No external oscillator
   - No USB

## Standard components
- Cost: Approximately $9.32 per board on JLCPCB (in quantities of 10) + ~$0.50 for a USB micro-B connector
  - $5.11 per board to use the STM32L151C8T6 instead of the STM32F103
  - $6.33 per board to use the STM32F302CBT6 instead of the STM32F103
- The components most likely to be needed for a typical application.
- Includes:
   - STM32F103C8T6 (U1)
   - Power regulator, power filtering capacitors, blocking diodes, ferrite bead (U2, C1-C8, D1, D2, L1)
   - Reset circuit (C9, S1)
   - Power LED (LED1, R7)
   - User LED (LED2, R8)
   - BOOT0/BOOT1 current-limiting resistors (R3/5)
   - External oscillator (Q1, C10)
   - Pull-up resistor on USB_DP (R1)
   - Shorting resistor to connect VBAT and VDD (R2)
- MCU can be powered from VDD (2-3.6V; >=2.4V if ADC is used), VIN (4.8-15V), or from USB1
- Includes 8 MHz oscillator
- User doesn't have to short any pads together (accomplished with a 0 ohm resistor, R2)
- User must populate J6/7 with a pin header and jumper in order to select the proper BOOT0/BOOT1 configuration
- Constraints:
   - No battery back-up

## Full components
- Cost: Approximately $10.01 per board on JLCPCB (in quantities of 10) + ~$0.50 for a USB micro-B connector
  - $5.80 per board to use the STM32L151C8T6 instead of the STM32F103
  - $7.02 per board to use the STM32F302CBT6 instead of the STM32F103
- Includes all components on the breakout board:
   - STM32F103C8T6 (U1)
   - Power regulator, power filtering capacitors, blocking diodes, ferrite bead (U2, C1-C8, D1, D2, L1)
   - Reset circuit (C9, S1)
   - Power LED (LED1, R7)
   - User LED (LED2, R8)
   - BOOT0/BOOT1 current-limiting resistors (R3/5)
   - External oscillators (Q1/2, C10/11)
   - Pull-up resistor on USB_DP (R1)
- MCU can be powered from VDD (2-3.6V; >=2.4V if ADC is used), VIN (4.8-15V), or from USB1
- Includes 8 MHz and 32.786 kHz oscillators
- User must populate J6/7 with a pin header and jumper in order to select the proper BOOT0/BOOT1 configuration
- User must connect battery (1.8-3.6V) to VBAT

# PCB Silkscreen Text
> - -------POWER-------
> - VDD/AVDD: 2-3.6V. Must be 3.3V if C39097/C387415 are used for Q1/Q2.
> - VUSB: 5V from USB1
> - VIN: 4.8-15V
> - BAT: 1.8-3.6V. Short R2 if unused.
> - **WARNING**: Do NOT power MCU from VDD if EITHER VIN or USB1 are also being used.
> - --------GPIO--------
> - Max current, ea pin: 25 mA
> - Max current, total: 150 mA OUT (minus MCU power, ~7-50 mA) and 150 mA IN (minus MCU power)
> - Bar on pin label=5V tolerant
> - USER LED (LED2) on PA3; Cut trace btwn J8 on BOTTOM of PCB to remove
> - --------BOM-------
> - All parts 0402 unless noted.
> - U1: STM32F103C8T6
> - U2: 2-3.6V regulator, >=150mA / SOT-223
> - J3: Debug Edge connector
> - J4: J-Link connector
> - Q1: 8MHz / 3.2x2.5mm
> - Q2: 32.768kHz / 3.2x2.5mm
> - L1: ferrite bead, 0805 (leave open for AVDD other MCU)
> - C3, C4, C5, C7-C11: 100nF
> - R3, R5: 10k | R8, R9: 150R
> - D1, D2: Shottky / SOD-123
> - LED1, LED2: 0603
> - R1: 1k5     | C6: 1uF
> - C1, C2: 10uF
> - S1: SPST-NO / 5.1mmx5.1mm
> - R2: 0R      | R4, R6: 0R (R4/6 pull BOOT0/BOOT1 to GND if J6/J7 not used)
> - FMI: github.com/nathancharlesjones/STM32F103C8T6-breakout-board

# References
- [STM32F103C8 product page](https://www.st.com/en/microcontrollers-microprocessors/stm32f103c8.html)
- [AN2586, Getting started with STM32F10xxx hardware development](https://www.st.com/resource/en/application_note/cd00164185-getting-started-with-stm32f10xxx-hardware-development-stmicroelectronics.pdf)
- [DS5319](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf), STM32F103C8 datasheet
- [RM0008](https://www.st.com/resource/en/reference_manual/cd00171190-stm32f101xx-stm32f102xx-stm32f103xx-stm32f105xx-and-stm32f107xx-advanced-armbased-32bit-mcus-stmicroelectronics.pdf), STM32F103 reference manual