# Proposal1 - Software

Current idea is to have two controllers

  1. The first being the one that handles motion control / lives on the control board (SKR 1.4)
  2. The second ether being a Rpi or ESP32 which hosts the wifi interface / handles button pushes / display
     Which can feed into the first board over uart or GPIO of some kind

## Main Board Firmware

Originally I looked into klpper since that might be the easiest to setup and get going without writing any custom software
But apparantly it doesn't work all that well when jogging, also it needs a full on Rpi

A couple of options would be

  1. RepRap Firmware - has been gotten to work with the SKR1.4 but not sure if that's the case for recent versions
  2. grbHal - not sure of it's limitations / capabilities
     https://github.com/grblHAL/Controllers

Nether would lead to a wifi interface on they're own
Although grbHal does list the SKR1.4 board as supported

## Wifi interface

For the wifi interface if using a SKR1.4 board

  1. Embedded Micro such as ESP32 / Rpi Pico Wireless to host the webui (custom) then feed instructions to the main board via it's Uart
  2. Full on Rpi such as a Raspberry Pi Compute Module 4 (£39.60)
     With this option ideally you'd want to make sure the filesystem was mounted readonly to prevent the SD card from burning out

## Screen / Buttons

For the Screen for an Rpi you can attach one to the ribbon cable output
For an embedded micro there's a bunch of different options

This one is the native BigtreeTech one, but it can't be wired directly to a 3.3V micro, it has to go via the SKR board

  * BIGTREETECH MINI 12864 V2.0 LCD Display Screen RGB backlight - £8.21
    https://www.aliexpress.com/item/1005006135086424.html

In so far as other switches / connectors there should be plenty on the SKR board or the secondary Controller depending on the setup


## Neeeded IO

  * 1 x Main Power Switch

  * 2 x Limit Switches (both ends of the table)
  * 1 x EStop Switch
  * 1 x screen maybe oled or LCD to show whats going on and the DRO
  * Toggle switch for jog/distance mode
  * Rotary encoder for the speed
  * Rotary encoder with fine tuning for the distance (or a keypad)
  * Left and right buttons - momentary in distance mode, hold down to jog mode
  * A toggle switch for mm/inch selection
  * A button to zero it

## TODO

  * are there any old Ender3's still nocking about that we could steal the control board from
  * Review the button / control layout on a diagram of some kind
