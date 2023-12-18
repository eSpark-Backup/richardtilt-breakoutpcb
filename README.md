# Richard Tilt - Breakout PCB Board Design

## Project Brief
The task requires observing the foorprints of various development kits that client intends to use and then creaing appropriate breakout board for these modules / kits for prototyping

## Project Requirements
- Create a breakout board with following components
    - 2 x Adafruit Feather Huzzah V2 ESP32 USB-C w.FL
    - 2 x w.FL Antenna
    - 2 x Sparkfun BabyBuck converters
    - 2 x Micro Switch
    - 1 x 16 Bit ADC
    - 1 x MatekSys PDB Hex
 - The whole project should be orderable from PCBWay
 - The PCB needs to be 90mm x 130mm
 - All connector spacings will be standard 2.54mm and connectors to use will be female.
 - On the PDB, the only part that is used is the double of pins above the JST connector, all the other large soldering pads go to brushless motors. Right side double row of 6 pins only (see image below)
 ![image](https://github.com/eSpark-Consultants/richardtilt-breakoutpcb/assets/76909080/7a2aab3a-a398-49d2-8b68-70ed474abf50)

### Desscription
The Source voltage comes from the PDB, a regulated 5V amount. The PDB will only connect to the PCB from a double row of six pins, see product description. The pins from the PDB are for the PWM signal (S2, S4 only), common ground, Vx (5V), Current Sensor. The PDB will connect to the PCB with only these pins, there is no high voltage / high current from the PDB to the PCB.

The Current pin from the PDB is used to monitor a current shunt. It is connected to A2 on the ADC. The Ground from the PDB is the main ground and is connected to all components, the 16 Bit ADC has several connections to this ground.

The Vx pin from the PDB is the main power supply for all components.

There is a VBat pin on the PDB - BUT - we will no be using that because it is 24V - instead, there is a 1/21 voltage divider on the surface of the PDB. A small 28 gauge wire for example, will be soldered from there to PCB.

There are 6 signal wires used to control PWM, use S2 and S4 only, which are pins on the PDB.

Between the Buck converter and the ESP32 is a simple switch. This switch allows to disconnect from the main circuit and use a USB-C
Cable to program / flash the ESP32 after installing on the PCB. Very Important!

There is a w.FL connector on each ESP32 (external antenna). Be careful, there is also another version with an on-board antenna, some of the product links for the w.FL version point to the version with the on board antenna. I will be using an external antenna so we need an M3 hole through the PCB. The antenna lead will PASS THROUGH the PCB. You can put the pass through hole of the PCB directly under the standoff hole on the lower left corner of the ESP32. The w.FL connector WILL fit through the standoff (M3?) hole of the ESP32 breakout board.

The 16 bit ADC is used to read the current sensor and the voltage divider from the PDB. The ADC connects to only one ESP32 using I2C.

Watch out for the TR / RX connection that exists between the 2 ESP32 boards. This is basically a UART connection so the 2 boards can communicate.

### Breakout board links
[Adafruit Feather Huzzah V2 ESP32 USB-C w.FL](https://www.adafruit.com/product/5438)
[2.FL Antenna](https://www.adafruit.com/product/5445)[
Sparkfun BabyBuck converters](https://www.sparkfun.com/products/18357)
[Micro Switch](https://www.sparkfun.com/products/102)
[Micro Switch datasheet](https://www.sparkfun.com/datasheets/Components/Buttons/P040040c.pdf)
[16 Bit ADC](https://www.amazon.com/HiLetgo-Converter-Programmable-Amplifier-Development/dp/B07VPFLSMX?ref_=ast_sto_dp)
[MakeSys PDB Hex](http://www.mateksys.com/?portfolio=pdb-hex)

### Draft for schematic design
![image](https://github.com/eSpark-Consultants/richardtilt-breakoutpcb/assets/76909080/25d69f7a-7a21-4e6f-92d9-59c1cce5c526)

Please note that left side contains actual module and pin info whereas right side is a legend!
 
### Reference images of components
![image](https://github.com/eSpark-Consultants/richardtilt-breakoutpcb/assets/76909080/eb340105-1888-4148-9247-f505f1579b3f)
