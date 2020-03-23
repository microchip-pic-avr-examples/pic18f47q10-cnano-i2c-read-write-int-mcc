<div id="readme" class="Box-body readme blob js-code-block-container">
 <article class="markdown-body entry-content p-3 p-md-6" itemprop="text"><p><a href="https://www.microchip.com" rel="nofollow"><img src="images/MicrochipLogo.png" alt="MCHP" style="max-width:100%;"></a></p>

# PIC18F47Q10 I2C Master Read/Write Data Using Interrupts

## Objective:
The PIC18F47Q10 configured in I2C Master Mode using the MSSP1 peripheral and performing read and write operations with interrupts. This example will use the slave [MCP23008](https://ww1.microchip.com/downloads/en/DeviceDoc/21919e.pdf), an I/O expander, addressed in 7-bit mode.

## Resources:
- Technical Brief Link [(linkTBD)](http://www.microchip.com/)
- MPLAB® X IDE 5.30 or newer [(microchip.com/mplab/mplab-x-ide)](http://www.microchip.com/mplab/mplab-x-ide)
- MPLAB® XC8 2.10 or newer compiler [(microchip.com/mplab/compilers)](http://www.microchip.com/mplab/compilers)
- MPLAB® Code Configurator (MCC) 3.95.0 or newer [(microchip.com/mplab/mplab-code-configurator)](https://www.microchip.com/mplab/mplab-code-configurator)
- PIC18F47Q10 Curiosity Nano [(DM182029)](https://www.microchip.com/Developmenttools/ProductDetails/DM182029)
- Curiosity Nano Base for Click Boards™ [(AC164162)](https://www.microchip.com/Developmenttools/ProductDetails/AC164162)
- 8-Bit I/O Expander with Serial Interface [(MCP23008)](https://ww1.microchip.com/downloads/en/DeviceDoc/21919e.pdf)
- PICkit™ Serial I2C™ Demo Board [(PKSERIAL-I2C1)](https://www.microchip.com/DevelopmentTools/ProductDetails/PKSERIAL-I2C1)
- [PIC18F47Q10 datasheet](http://ww1.microchip.com/downloads/en/DeviceDoc/40002043D.pdf) for more information or specifications.

## Hardware Configuration:

The PIC18F47Q10 Curiosity Nano Development Board [(DM182029)](https://www.microchip.com/Developmenttools/ProductDetails/DM182029) is used as the test platform, along with the Curiosity Nano Base for Click Boards™ [(AC164162)](https://www.microchip.com/Developmenttools/ProductDetails/AC164162) and PICkit™ Serial I2C™ Demo Board [(PKSERIAL-I2C1)](https://www.microchip.com/DevelopmentTools/ProductDetails/PKSERIAL-I2C1).

### MSSP1 configuration:
- Interrupt Driven
- I2C Master Mode
- I2C Clock Frequency: 100000

### Pin configuration:
- RB1 pin - digital, with internal pull-up, used as SCL
- RB2 pin - digital, with internal pull-up, used as SDA

## Demo:
PICkit™ Serial I2C™ Demo Board will be used to demonstrate this project. This board contains the slave [MCP23008](https://ww1.microchip.com/downloads/en/DeviceDoc/21919e.pdf) with LEDs connected to all extended pins. 

The extended pins are set as digital output with an I2C write operation in the *IODIR* register. After the pins are set, the program will repeatedly:
- set pins to `DATA` value, with an I2C write operation in the *GPIO* register
- set `DATA` to the value read from the *GPIO* register, with an I2C read operation
- invert the bits in `DATA`

The initial value of `DATA` will be *0x0F*, and the program will continously toggle each half of the LEDs.

</br></br>

<img src="images/rw-int.gif"  width="600px" alt="Hardware Setup"/>
