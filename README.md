# WHITEBoard-White-Pill

![20220412_215704](https://user-images.githubusercontent.com/30090189/163045645-aa4f2956-966f-4322-9561-b9d8e3687291.jpg)

WHITEBoard White Pill is a development board based on STM32F030C8T6. Development board has all features that this microcontroller offers, plus some aditional. In this repo you will find all the data you need to make this board, that include schematic, gerber files, etc. In adition, there are examples for all features this White Pill variant offers.

## Features

* STM32F030C8T6
  * Arm® 32-bit Cortex®-M0 CPU, frequency up to 48 MHz
  * 64 Kbytes of Flash memory
  * 8 Kbytes of SRAM with HW parity
  * 2x I2C, 2x SPI, 3x USART, SWD
* All GPIO pins breaks into two header rows
* UART CH340
* User Buttons
  * BOOT
  * RST
* Li-Po JST connector with MCP73831 charging circuit
* Micro USB UART port
* Power switch

![20220412_215714](https://user-images.githubusercontent.com/30090189/163045813-c8349257-f7b2-45ed-ab17-76061f5916f9.jpg)

## Getting started

WHITEBoard White Pill is a development board that can be programmed through Arduino IDE. Arduino IDE package can be installed from here: https://github.com/stm32duino/Arduino_Core_STM32

Upload selection:
* Board: Generic STM32F0 Series
* Board Part Number: Generic F030C8Tx
* U(S)ART Support: Disabled (no Serial Support)
* Upload method: STM32CubeProgrammer (Serial)

![20220412_215727](https://user-images.githubusercontent.com/30090189/163047067-d7906aa4-a06d-4999-87b3-9974f1c063cc.jpg)

## Power

For power management, this board uses two ICs. MCP73831 For battery management check the LiPo charging section below.
WHITEBoard White Pill can be powered up by the micro USB connectors. 5V rail is going to the SE5218 voltage regulator. This is an LDO that provides 3.3V@500mA. While testing, I had ZERO issues with stability. But it also means that WHITEBoard White Pill can not directly power up some power-hungry sensors or modules. In such a case, use an external power supply.
There is no dedicated VIN pin to power WHITEBoard White Pill through pinout. However, pin 5V can be used to power WHITEBoard White Pill with REGULATED 5V DC. Do not use pin 3V3 in a similar manner. However, you CAN NOT charge battery through 5V pin.
The switch under the board is manipulating with the EN pin of the LDO. This way powers up the board. There is a MOSFET for switching the power supply. WHITEBoard White Pill will cut the battery when there is 5V power on micro USBs or 5V pin. Charging the battery remains all the time when there is 5V. The same goes for the power switch position.

## LiPo charging

For Li-Po charging there is the MCP73831 IC. With a resistor R8 of 2K, charging is set to 500mA charging current. By replacing this resistor you can change the charging current. Here is the table:
* 10K - 100mA
* 5K  - 200mA 
* 2K  - 500mA
* 1K  - 1000mA

Onboard there is a JST 2.00mm pitch connector. As JST is NOT standardized, please check the battery polarity. Wrong polarity can destroy the board and/or battery. Supported batteries are standard Li-Ion/Li-Po with 3.7V nominal voltage. You can use a battery of any capacity.

If the project is for use with a battery, there is a switch on the right side that basically switch from VCC to GND on the EN pin of a voltage regulator. This way you can enable or disable power to the BOARD. In case you can not upload the sketch to a WHITEBoard White Pill, please check the position of this switch. While turned OFF by this switch, you can still charge the battery by the micro USB port.

## Pinout

WHITEBoard White Pill has a two-row header with 42 pins in total. Here you can find the boards diagram so check it out. As I mention, WHITEBoard White Pill has all STM32F030C8T6 pins break out. That is the reason for the size of the board, besides 0805 components and soldering on one side only. To power additional sensors and modules, there are two GND pins and two power pins (5V and 3.3V). There is no VIN pin (check the Power part above). For interfacing I2C, I2S, SPI, etc. please check the datasheet https://www.st.com/resource/en/datasheet/stm32f030f4.pdf

* First Row
  * C13
  * C14
  * C15
  * A0
  * A1
  * A2
  * A3
  * A4
  * A5
  * A6
  * A7
  * B0
  * B1
  * B2
  * B10
  * B11
  * RST
  * 3V3
  * GND
  * 5V
* Second Row
  * B9
  * B8
  * B7
  * B6
  * B5
  * B4
  * B3
  * A15
  * CLK
  * F7
  * F6
  * DIO
  * A12
  * A11
  * A10
  * A9
  * A8
  * B15
  * B14
  * B13
  * B12
  * GND
   
## Dimensions
Dimensions: (25.4 × 80.0 × 7.5) mm.

## Disclaimer

WHITEBoard White Pill is an open-source development board. My small contribution to the community, that gave me so much. Feel free to use and modify as you want. It would be nice to add some credits if you do.
