# Knowing Components

* Flight Controller:
    * CrazyBee Pro V2 F4FS `CRAZYBEEF4FS`
        * V3 now available
    * Betaflight Version: 4.0.6 `2A64051` -> 4.1.2 (Legacy)
    * Processor: STM32F

* Receiver:
    * FLYSKY AFHDS 2A Version

* Transmitter:
    * FLYSKY i6 - [Can upgrade to support more channels](https://github.com/qba667/FlySkyI6/wiki) (Note - wiring diagram on install page has correct labels, but tx and rx were other way round vs lines in diagram on rs232 board. Also use 3.3v mode.)


* ESC:
  * S-H-50 - key here is `H`
  * 16-bit ESC (can use BLHELI or BLHELI_S, [not BLHELI_32](https://4in1esc.com/articles/blhelis-vs-blheli32) )
  * Factory Firmware: BLHELI_S 16.7

* Motors:
  * TC0803 - KV15000 - snappy but thin spindle which is easy to bend


# Initial Setup
## Installing Drivers

1) USB virtual COM port driver [here](https://www.st.com/en/development-tools/stsw-stm32102.html#get-software) (used bugmenot to get site login)

2) STM Bootload Driver - this is installed by default with W10?

3) Zadig - lets you select the driver for a device

## Binding


# Flight Config
Adding a rateprofile with a scaled throttle limit of 0.7 and setting Exp to 0.5 will give a much more manageable setup for flying indoors.

[Tips on flying indoors](https://blog.georgi-yanev.com/fpv/unbox-review-setup-eachine-trashcan/#flying-indoors)

# Updating

Saw following video after googling hot motors:
https://www.youtube.com/watch?v=krf_M-csJ60

This comment piqued my interest:

>Hi, you really have to do it 😃 I stopped flying with my Trashcan about 6 months ago because of bad flight time and bad propwash, now on BF4.1.1 & **RPM filters** and a free version of JazzMac's **48kHz ESC firmware** I have a new high performing Trashcan 😃
Here is the RCG forum about JazzMac's free ESC firmware upgrade:
https://www.rcgroups.com/forums/showthread.php?2640796-BLHeli_S-Smooth-as-Silk/page366
GitHub link for the firmware:
https://github.com/JazzMaverick/BLHeli/tree/JazzMaverick-patch-1/BLHeli_S%20SiLabs



## New Version of Betaflight

[DSHOT & RPM Filter Wiki](https://github.com/betaflight/betaflight/wiki/Bidirectional-DSHOT-and-RPM-Filter) :
>These two features are supported by BetaFlight 4.1 on all flight controllers, and most modern BLHeli_32 and *BLHeli-S ESCs*. Betaflight 4.0 is no longer supported.

[Installing BetaFlight](https://github.com/betaflight/betaflight/wiki/Installing-Betaflight)

The trashcan is a type 2 Device:
> Type 2. Using the MCU integrated STM32 VCP USB interface.
2.1 Needs WinUSB driver when in BootLoader mode, for flashing. Installed by Zadig or ImpulseRC DF. Shows up as a "DFU" device in BFC.
2.2 Needs STM VCP driver for connection and configuration with BFC Shows up as a "COMx" device in BFC.


[BetaFlight USB Flashing Wiki](https://github.com/martinbudden/betaflight/blob/master/docs/USB%20Flashing.md)

Note down settings beforehand and then recreate them in new betaflight - dont try to import settings from a different version of betaflight, caused lots of issues.

## ESC Firmware
Factory Firmware: https://www.mediafire.com/folder/dx6kfaasyo24l/BLHeliSuite

Options for updates:
* [BLHELI_S](https://www.rcgroups.com/forums/showthread.php?2640796-BLHeli_S-Smooth-as-Silk)
    * FOSS
    * Original firmware for the Trashcan
    * Does not support rpm filter
* [JAZZ_MC](https://github.com/JazzMaverick/BLHeli/tree/JazzMaverick-patch-1/BLHeli_S%20SiLabs) (fork of BLHELI_S)
    * FOSS
    * Betaflight Wiki recommends using 16.73 version as a free option
* [JESC](https://jflight.net/):
    * PAID, but not expensive and done by the guy who implemented the rpm filter in betaflight.


> JESC supports bidirectional DSHOT and RPM Filter on BLHeli_S escs. Free on L ESCs, Paid but VERY cheap and worth it on H ESCs! 48khz and 96khz PWM version available for testing Get it here!
