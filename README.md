# STM32F103C8T6 Breakout Board
![](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/master/STM32F103C8T6_PCB.png)

# How to order
1. Download or clone this repository.
2. Choose which components you want to include on your breakout board. If it's not one of the prepared arrangements below (Minimum, Standard, or Full), edit the bill of materials ("bom") and assembly files to include only those components that you want. The easiest way to do this is probably to start with the "Full" lists and simply delete the rows of the components you don't want to include.
3. Follow [these instructions for ordering an assembled PCB from JLCPCB or MakerFabs](https://github.com/nathancharlesjones/Embedded-for-Everyone/wiki/3.-Building-a-circuit-on-a-PCB-and-connecting-it-to-the-rest-of-the-embedded-device#ordering-an-assembled-pcb).

# STM32F103C8T6 specifications
|Processor|Core Size|Speed|Connectivity|Peripherals|I/O|Program memory size|RAM size|Data converters|
|---|---|---|---|---|---|---|---|---|
|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|64 kB|20 kB|ADC: 10x 12-bit|

# Pin-compatibility

**WARNING**: I have not checked each of these parts and cannot guarantee that they will work with this board without modifications. They are listed here merely to bring to the reader's attention that there _may_ be pin-compatible STM32 MCUs which _could_ work with this board in the event that the STM32F103C8T6 is not exactly the MCU they would like to use. If you are interested in using one of these other MCUs, I would recommend that you find the appropriate datasheet and hardware development guide from ST Microelectronics to ensure that this board will meet the requirements of any new MCU.

Using the STM32CubeMX tool, it appears to me that, as of this writing (30 Dec 2020), this board is also exactly pin-compatible with the MCUs below (the STM32F103C8Tx is shown in the first row for comparison).

|Part No.|Processor|Core Size|Speed|Connectivity|Peripherals|I/O|Program memory size|RAM size|Data converters|
|---|---|---|---|---|---|---|---|---|---|
|STM32F103C8Tx|ARM Cortex-M3|32-bit|72 MHz|I2C, SPI, UART/USART, USB, CANbus, IrDA, LINbus|DMA, Motor Control PWM, PDR, POR, PVD, PWM, Temp Sensor, WDT|37|64 kB|20 kB|ADC: 10x 12-bit|
|STM32F102C4Tx|
|STM32F102C6Tx|
|STM32F102C8Tx|
|STM32F102CBTx|
|STM32F103C4Tx|
|STM32F103C6Tx|
|STM32F103CBTx|
|STM32F302C6Tx|
|STM32F302C8Tx|
|STM32F302CBTx|
|STM32F302CCTx|
|STM32F303CBTx|
|STM32F303CCTx|

v Different power pins? v
|STM32F373C8Tx|
|STM32F373CBTx|
|STM32F373CCTx|

JLCPCB STM32 in QFP-48
- 

VFQFN & QFP36

The following MCUs are pin-compatible for the purposes of this breakout board (meaning the power, programming, and clock pins line up), but may map their peripherals to different pins than the STM32F030F4P6. From what I could see, it appears as though the only difference is that these MCUs use a different port for the clock pins than the previous MCUs; they will still work as clock pins, but offer slightly different alternate functions than do the MCUs above. The STM32F030F4P6 is shown in the first row (again) for comparison.

|Part No.|Processor|Core Size|Speed|Connectivity|Peripherals|I/O|Program memory size|RAM size|EEPROM size|Data converters|
|---|---|---|---|---|---|---|---|---|---|---|
|STM32F030F4Px|ARM Cortex-M0|32-bit|48 MHz|I2C, SPI, UART/USART|DMA, POR, PWM, WDT|15|16 kB|4 kB|N/A|ADC: 11x 12-bit|
|STM32L010F4Px|ARM Cortex-M0+|32-bit|32 MHz|I2C, SPI, UART/USART, IrDA|DMA, POR, PWM, WDT, Brown-out detect/reset|16|16 kB|2 kB|128 bytes|ADC: 7x 12-bit|

# Schematic
![](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/main/Supporting-documentation/STM32F103C8T6-breakout-board_schematic.png)

The schematic for this breakout board includes 7 modules or sections:
1. MCU
   - The MCU itself and the 0.1" pin headers to which the MCU pins are connected (U1 and J1/J2).
2. Power & USB
   - Power: Power regulator, power filtering capacitors, diode protection, LED indicator, and shorting resistor/ferrite bead (U2, D1, D2, C1-C8, LED1, R1, L1/R2).
   - USB: USB connector and pull-up resistor on USB_DP (USB1 and R1).
   - VDD is 2-3.6V (or 2.4-3.6V if the ADC is used).
   - Only C2-C8 and L1 are technically required for MCU operation.
   - If U2 is used, D1 and D2 are strongly recommended, though not technically required. D1 and D2 allow for the MCU to be powered from both the VIN_4.8-15V pin and USB1 connector at the same time without them damaging each other.
   - VDD/AVDD can serve as power inputs (if NEITHER VIN_4.8-15V NOR USB1 are used) or as a power output (if EITHER VIN_4.8-15V OR USB1 are used). Do NOT attempt to power the MCU from VDD if EITHER VIN_4.8-15V OR USB1 are used; the output of the voltage regulator (U2) is tied directly to VDD and one power source may back-power the other.
   - VBAT (1.8-3.6V) provides a battery back-up for the MCU.
     - If you **DO** intend to use this feature, leave R2 open.
     - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R2 (or simply short the pads together) to connect VBAT to VDD.
     - For some of the pin-compatible MCUs (such as the STM32L151 MCU that I first tested this PCB with), "VBAT" becomes "VLCD", which controls the contrast of a connected LCD. See the appropriate datasheet/hardware development guide for further details.
   - AVDD is the power supply for the MCU's analog circuitry. For the STM32F103C8T6, AVDD should be at the same voltage as VDD. A ferrite bead, L1, connects the two together while providing some protection from high-frequency noise.
     - For some of the pin-compatibe MCUs, AVDD is allowed to be a different voltage from VDD. If you use one of those MCUs and intend to use a different AVDD, then leave L1 open.
3. Reset
   - The reset button and smoothing capacitor (S1 and C9).
4. BOOT0/BOOT1
   - Selection pin headers, current-limiting resistors, and pull-down resistors (J6/7, R3/5, and R4/6)
   - BOOT0/BOOT1 select which part of the MCU's memory is run at start-up (see [AN2586, Getting started with STM32F10xxx hardware development](https://www.st.com/resource/en/application_note/cd00164185-getting-started-with-stm32f10xxx-hardware-development-stmicroelectronics.pdf) for more details).
   - If you **DO** intend to use this feature, leave R4/6 open.
   - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R4/6 (or simply short the pads together) to pull BOOT0/BOOT1 to ground.
5. External oscillators
   - Crystal oscillators and power capacitors (Q1/2, C10/11)
   - An external crystal oscillator will have higher accuracy than the internal clock, which improves the accuracy of the internal timers and may be necessary for applications such as high-speed UART, USB, and RTC.
6. User LED
   - LED, current-limiting resistor, and option jumper (LED2, R8, and J8)
   - J8 is used to optionally remove the LED from the circuit, should you wish to not have the LED connected to its GPIO.
   - To remove LED2 from the circuit, cut the trace between the terminals of J8 on BOTTOM of the PCB (where its marked on the silkscreen).
   - To reinsert LED2, place a pin header and jumper in J8. The jumper now controls whether LED2 is included in the circuit or not.
7. J-Link and Debug Edge connectors (J3/4)
   - J4 is configured to match the pinout of the 10-pin connector on the J-Link Edu Mini.
   - J3 is intended for use with a series of board-to-board connectors by AVX, popularly called ["Debug Edge"](www.debug-edge.io). The purpose, once an [adapter board](https://github.com/nathancharlesjones/Debug-Edge_SWD-to-J-Link-Edu-Mini-adapter-with-USB-power) is acquired, is to save the developer from having to purchase J4 for development with the J-Link Edu Mini. The adapter board mentioned previously also includes a USB connector for powering the MCU (connects directly to VDD and so should not be used when VIN_4.8-15V or USB1 are also used).

## Minimum components
- Cost: Approximately $2.60 per board on JLCPCB (in quantities of 10)
- The minimum components required for the MCU to operate plus a reset button, power LED, and user LED.
- Includes:
   - STM32F030F4P6 (U1)
   - Power filtering capacitors (C2, C3)
   - Reset circuit (C8, S1)
   - Power LED (LED1, R1)
   - User LED (LED2, R2)
   - BOOT0 current-limiting resistor (R4)
- User must short the pads of D3 and (separately) the pads of R5.
- Constraints:
   - Analog reference voltage (VDDA) is equal to the power supply voltage (VDDA)
   - Power supply voltage must be 2.4-3.6V
   - BOOT0 fixed at 0 (unless a logical 1 is present on the BOOT0 pin on J1)
   - No external oscillator

## Standard components
- Cost: Approximately $3.00 per board on JLCPCB (in quantities of 10)
- The components most likely to be needed for a typical application.
- Includes:
   - STM32F030F4P6 (U1)
   - Power regulator, power filtering capacitors, and blocking diodes (IC1, C1, C2, C3, D1, D2)
   - Reset circuit (C8, S1)
   - Power LED (LED1, R1)
   - User LED (LED2, R2)
   - BOOT0 current-limiting resistor and pull-down resistor (R4, R5)
   - External oscillator (Y1, C6, C7, R3)
   - Shorting resistor across D3
- Power supply can be 2.4-3.6V (on VIN_2.4-3.6V) or 5-30V (on VIN_5-30V)
- User doesn't have to short any pads together (all accomplished with two 0 ohm resistors, R5 and "D3")
- Constraints:
   - Analog reference voltage (VDDA) is equal to the power supply voltage (VDDA)
   - BOOT0 fixed at 0 (unless a logical 1 is present on the BOOT0 pin on J1)

## Full components
- Cost: Approximately $3.00 per board on JLCPCB (in quantities of 10)
- Includes all components on the breakout board:
   - STM32F030F4P6 (U1)
   - Power regulator, power filtering capacitors, and blocking diodes (IC1, C1, C2, C3, D1, D2)
   - Reset circuit (C8, S1)
   - Power LED (LED1, R1)
   - User LED (LED2, R2)
   - BOOT0 current-limiting resistor (R4), **NO** shorting resistor
   - External oscillator (Y1, C6, C7, R3)
   - Analog voltage reference diode and power filtering capacitors (D3, C4, C5)
- Power supply can be 2.4-3.6V (on VIN_2.4-3.6V) or 5-30V (on VIN_5-30V)
- User must populate J2 with a pin header and jumper in order to select the proper BOOT0 configuration
- Board may, but is not required to, run a separate power supply voltage and analog reference voltage.

# PCB Silkscreen Text
> -------POWER-------
> VDD/AVDD: 2-3.6V. Must be 3.3V if C39097/C387415 are used for Q1/Q2.
> VUSB: 5V from USB1
> VIN: 4.8-15V
> BAT: 1.8-3.6V. Short R2 if unused.
> **WARNING**: Do NOT power MCU from VDD if EITHER VIN or USB1 are also being used.
> --------GPIO--------
> Max current, ea pin: 25 mA
> Max current, total: 150 mA OUT (minus MCU power, ~7-50 mA) and 150 mA IN (minus MCU power)
> Bar on pin label=5V tolerant
> USER LED (LED2) on PA3; Cut trace btwn J8 on BOTTOM of PCB to remove
> --------BOM-------
> All parts 0402 unless noted.
> U1: STM32F103C8T6
> U2: 2-3.6V regulator, >=150mA / SOT-223
> J3: Debug Edge connector
> J4: J-Link connector
> Q1: 8MHz / 3.2x2.5mm
> Q2: 32.768kHz / 3.2x2.5mm
> L1: ferrite bead, 0805 (leave open for AVDD other MCU)
> C3, C4, C5, C7-C11: 100nF
> R3, R5: 10k | R8, R9: 150R
> D1, D2: Shottky / SOD-123
> LED1, LED2: 0603
> R1: 1k5     | C6: 1uF
> C1, C2: 10uF
> - S1: SPST-NO / 5.1mmx5.1mm
> - R2: 0R      | R4, R6: 0R (R4/6 pull BOOT0/BOOT1 to GND if J6/J7 not used)
> - FMI: github.com/nathancharlesjones/STM32F103C8T6-breakout-board

# References
- [STM32F030F4 product page](https://www.st.com/content/st_com/en/products/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus/stm32-mainstream-mcus/stm32f0-series/stm32f0x0-value-line/stm32f030f4.html)
- [AN4325, Getting started with STM32F030xx and STM32F070xx series
 hardware development](https://www.st.com/content/ccc/resource/technical/document/application_note/91/66/2d/8c/f9/b5/47/55/DM00089834.pdf/files/DM00089834.pdf/jcr:content/translations/en.DM00089834.pdf)
- [DS9773](https://www.st.com/resource/en/datasheet/stm32f030f4.pdf), STM32F030F4P6 datasheet
- [RM0360](https://www.st.com/resource/en/reference_manual/dm00091010.pdf), STM32F030F4P6 reference manual