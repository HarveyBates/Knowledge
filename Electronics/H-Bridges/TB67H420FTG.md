# TB67H420FTG (H-Bridge Motor / TEC Driver)
## Description
Instructions on how to wire up a TB67H420FTG H-Bridge motor driver for motors and thermoelectric coolers (peltier modules).

## Resources

Pololu website guide:

URL: https://www.pololu.com/product/2999

Video on connecting motor driver to Teensy:

URL: https://youtu.be/LH3bHMQEy7U

# Setup
## Wiring
### Single Motor Control

```INA1``` = a digital pin

```INA2``` = a digital pin

```PWMA``` = a digital pin

```GND``` = Ground

**Do not connect VCC to teensy as this is a regulated *output* from the motor input voltage!**

```A+ and A-``` = should be connected together via a jumper

```B+ and B-``` = should be connected together via a jumper

```VIN``` = supply voltage (normally 12 V)

```HBMode``` = should be connected to VCC (5 V) via a jumper

#### Pin Table

![Pin_Table](../imgs/TB67H420FTG_Pins.png)


#### Truth Table

![Truth_Table](../imgs/TB67H420FTG_Truth_Table.png)

#### Current Limiting 
The TB67H420FTG can actively limit the current through the motors by using a fixed-frequency PWM current regulation (current chopping). This carrier board connects voltage dividers to the VREFA and VREFB pins that set the reference voltage to about 3.6 V.

In single-channel mode, the default 3.6 V reference voltage results in a nominal single-channel current limit of 9 A. The formula for the current chopping threshold in single-channel mode is Iout=VREF×2.5.


