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
|STM32F373C8Tx|
|STM32F373CBTx|
|STM32F373CCTx|


The following MCUs are pin-compatible for the purposes of this breakout board (meaning the power, programming, and clock pins line up), but may map their peripherals to different pins than the STM32F030F4P6. From what I could see, it appears as though the only difference is that these MCUs use a different port for the clock pins than the previous MCUs; they will still work as clock pins, but offer slightly different alternate functions than do the MCUs above. The STM32F030F4P6 is shown in the first row (again) for comparison.

|Part No.|Processor|Core Size|Speed|Connectivity|Peripherals|I/O|Program memory size|RAM size|EEPROM size|Data converters|
|---|---|---|---|---|---|---|---|---|---|---|
|STM32F030F4Px|ARM Cortex-M0|32-bit|48 MHz|I2C, SPI, UART/USART|DMA, POR, PWM, WDT|15|16 kB|4 kB|N/A|ADC: 11x 12-bit|
|STM32L010F4Px|ARM Cortex-M0+|32-bit|32 MHz|I2C, SPI, UART/USART, IrDA|DMA, POR, PWM, WDT, Brown-out detect/reset|16|16 kB|2 kB|128 bytes|ADC: 7x 12-bit|

# Schematic
![](https://github.com/nathancharlesjones/STM32F103C8T6-breakout-board/blob/master/STM32F103C8T6_Schematic.png)

The schematic for this breakout board includes 8 modules or sections:
1. MCU
   - The MCU itself and the 0.1" pin header to which most of the MCU pins are connected (U1 and J1).
2. Power 
   - Power regulator, power filtering capacitors, and an LED indicator (IC1, D1, D2, C1, C2, C3, LED1, and R1).
   - Only C2 and C3 are technically required for MCU operation. If you decide to only include those two components, don't forget to bridge the pads of D1.
   - If IC1 is used, D1 and D2 are strongly recommended, though not technically required. D1 and D2 allow for the MCU to be powered from both the VIN_2.4-3.6V and VIN_5-30V pins at the same time without them damaging each other.
3. Reset
   - The reset button and smoothing capacitor (S1 and C8).
4. BOOT0
   - Selection pin header, current-limiting resistor, and pull-down resistor (J2, R4, and R5)
   - BOOT0 selects which part of the MCU's memory is run at start-up (see [AN4325, Getting started with STM32F030xx and STM32F070xx series
 hardware development](https://www.st.com/content/ccc/resource/technical/document/application_note/91/66/2d/8c/f9/b5/47/55/DM00089834.pdf/files/DM00089834.pdf/jcr:content/translations/en.DM00089834.pdf) for more details).
   - If you **DO** intend to use this feature, leave R5 open.
   - If you **DON'T** intend to use this feature, use a 0 ohm resistor for R5 (or simply short the pads together) to pull BOOT0 to ground.
5. External oscillator
   - Crystal oscillator, load capacitors, and feedback resistor (Y1, C6, C7, and R3)
   - An external crystal oscillator will have higher accuracy than the internal clock, which improves the accuracy of the internal timers and may be necessary for applications such as high-speed UART.
6. Analog voltage reference (VDDA)
   - Diode and power filtering capacitors (D3, C4, and C5)
   - Useful when you want to run the MCU at a lower voltage than what you want your analog voltage reference to be.
   - VDDA **MUST BE** higher than or equal to VDD (hence the diode; it ensures VDDA is at least equal to VDD during power-up/power-down).
   - If you **DON'T** intend to have a separate analog reference voltage, you can leave C4 and C5 off and replace D3 with a 0 ohm resistor (or simply short the pads together). If you do that, be careful not to power the MCU from the VDDA pin in addition to either of the VIN pins. If the power supply voltage on the VIN pins exceeds that of the power supply on the VDDA pin, then the VIN power supply may backpower the VDDA power supply and damage it.
7. User LED
   - LED, current-limiting resistor, and option jumper (LED2, R2, and J3)
   - J3 is used to optionally remove the LED from the circuit, should you wish to not have the LED connected to its GPIO.
   - To remove LED2 from the circuit, cut the trace between the terminals of J3 on TOP of the PCB (where its marked on the silkscreen).
   - To reinsert LED2, place a pin header and jumper in J3. The jumper now controls whether LED2 is included in the circuit or not.
8. J-Link connector (J4)

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
> - VIN, 2.4-3.6V: MCU damage may occur if >4V
> - Max current, ea pin: 25 mA
> - Mx current, all pins: 80 mA
> - USER LED on A0 (pin 6); Cut trace btwn J3 on TOP of PCB to remove LED (in-stall jumper to reinsert)
>--------------------
> - U1: STM32F030F4P6
> - IC1: 2.4-3.6V regulator, >=100mA / SOT-89-3 (ex: LCSC part# C14289)
> - Y1: 8MHz resonator / 5x3.2mm (ex: LCSC part# C115962)
> - J2: J-Link connector (ex: HPH2-A-10-UA from Adam Tech or 3220-10 -0100-00 from CNC Tech)
> - All footprints other parts 0603 unless noted.
> - C1: 10uF        | C2: 4.7uF
> - C3, C8: 100nF   | C4: 1uF
> - C6, C7: 20pF    | C5: 10nF
> - R5: 0R (pulls BOOT0 to GND if J2 is not used)
> - R3: 1k
> - R1, R2: ~100R   | R4: 10k
> - S1: SPST-NO / 5.1mmx5.1mm (ex: LCSC part# C318884)
> - D1, D2: Shottky / SOD-123
> - D3: Shottky / DO-214AC (short if VDDA = VDD)
> - FMI: github.com/nathancharlesjones/Embedded-for-Everyone/wiki

# References
- [STM32F030F4 product page](https://www.st.com/content/st_com/en/products/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus/stm32-mainstream-mcus/stm32f0-series/stm32f0x0-value-line/stm32f030f4.html)
- [AN4325, Getting started with STM32F030xx and STM32F070xx series
 hardware development](https://www.st.com/content/ccc/resource/technical/document/application_note/91/66/2d/8c/f9/b5/47/55/DM00089834.pdf/files/DM00089834.pdf/jcr:content/translations/en.DM00089834.pdf)
- [DS9773](https://www.st.com/resource/en/datasheet/stm32f030f4.pdf), STM32F030F4P6 datasheet
- [RM0360](https://www.st.com/resource/en/reference_manual/dm00091010.pdf), STM32F030F4P6 reference manual