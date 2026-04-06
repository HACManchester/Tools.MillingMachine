# Proposal 1 - Hardware

## Stepper Driver

The original stepper driver proposed by Ammiel was a DM542T
This is for a 48V nema 23 3NM stepper

For the stepper driver one idea is to use the BigTreeTech TMC5160T

  * https://www.aliexpress.com/item/1005006015265763.html
  * https://github.com/bigtreetech/BIGTREETECH-Stepper-Motor-Driver/tree/master/TMC5160T%20Plus
  * https://biqu.equipment/products/bigtreetech-tmc5160-v1-0-driver-spi-mode-silent-high-precision-stepstick-stepper-motor-driver-with-heatsink-for-skr-v1-3-gen-v1-4-reprap
  * Cost - £42.39

This supports up to 60V / 10A RMS / 15A Peak
It's a Trinamic Driver which means it has support for setting options via SPI for things like StealthChop / SpreadCycle for smoother motion
It also has optional support for an encoder (I think 32bit not sure of the spec)
And 256 Microsteps

## 4th Axis

We have access to a 4th Axis stepper / 3 jaw chuck which could be useful on the milling machine
So an additional secondary stepper driver and control for this could be useful at the same time
This probably wouldn't need to be as powerful as the one for the powerfeed (unless we put a bigger stepper motor on it)

## Control Board

Another idea is to try and use other BTT Hardware since it's cheap and compatible with the above
For the Control Board

  * SKR V1.4 
  * https://www.aliexpress.com/item/4000470048293.html
  * Cost - £25

By itself this doesn't have wireless / wifi so would need external control buttons
or some form of Uart in from a secondary controller such as a ESP32 or Rpi

## Power Supply

For the power supply this will be 48V for the High voltage side (the main one to driver the stepper)
Max current draw is up to 10A RMS 15A Peak for the driver
but not sure what max current the motor needs, will be less than this I'd guess

FYI 48V x 10A = 480W

We also need a secondary 24V to feed into the SKR board
We're not powering any heaters or onboard steppers so shouldn't need that much
for the single stepper board this takes 24V in then uses it for a Fan and feeds into a 78L12 which has a max current output of 100mA

## Other Hardware

  * Stepper Motor - ?

  * 48V Power supply - ?
    (wattage will be 48V / Needed Amps which will depend on stepper)

  * 48V to 24V buck converter (for Fans and stepper / control board)
    (not sure about this one seems a bit too cheap)
    https://www.aliexpress.com/item/1005006655489823.html
    Cost £1.57

  * ESP32 or Rpi to act as a wifi interface?
    May depend on the software stack

## TODO

  * What is the max current of the stepper driver
  * designs for coupling to the X Axis
