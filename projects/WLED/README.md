# WLED

WLED is an open-source firmware designed to control addressable LED strips such as NeoPixel (WS2812B, WS2811, SK6812) and some SPI-based chipsets using ESP32 or ESP8266 microcontrollers. It runs a web server on these devices, allowing users to manage LED colors, effects, and configurations through an intuitive web interface or mobile apps

## Quick Start

- Quick start guide - https://kno.wled.ge/basics/getting-started/

## Installation - (Binary)


- Installation Guide -  https://kno.wled.ge/basics/install-binary/

- Binary Releases - https://github.com/wled/WLED/releases


**ESP8266** - Flash command using esptool

```esptool.py write_flash 0x0 ./WLED_XXX.bin```

**ESP32**


1. Firstly, flash the version 4 bootloader file, which you can find [here](https://github.com/Aircoookie/WLED/releases/download/v0.13.1/esp32_bootloader_v4.bin).

This step only has to be done once, to update afterwards the bootloader does not have to be re-installed.

```esptool.py write_flash 0x0 ./esp32_bootloader_v4.bin```

2. Now you can flash the actual firmware binary. Keep in mind the bootloader needs to have a flash offset of 0, but the firmware 0x10000.

```esptool.py write_flash 0x10000 ./WLED_XXX.bin ```

3. When esptool.py says Connecting..., some ESP32 boards require you to hold the boot button (to the right of the USB port) for a few seconds

If you experience issues, run this command before trying write_flash again (Note: this will erase all settings stored on the ESP!)

```python -m esptool --chip esp32 erase_flash```

## Connection

1. Use a WiFi device to connect to the access point WLED-AP using the default password wled1234. You can also just scan this QR code:

    ![Qrcode](https://i.ibb.co/h2YswXK/WLED-QR-Connect-WB.png)

2. (or) Go to the IP 4.3.2.1 in your browser to control your lights! You should also be able to connect to wled.me if in access point mode (embedded DNS server).



## My Project Details:


1. Don't have addressable LED.

2. Don't have MOSFET (transistor) and resistors

3. I just having ESP8266 (a Node MCU Board about ₹170) , laptop and one RGB LED (HW- 478)





so, i have to change the LED Prefrences in web server

**My Changes**


- In the WLED web interface, go to Config > LED Preferences.

- Set "LED Output" to "PWM/Analog".

- Assign the correct GPIO numbers (not Dx labels!) for R, G, and B. For example:

    1. Red: 14

    2. Green: 12

    3. Blue: 13

- Set the number of LEDs to 1.


**HW-478 Pin Mapping for WLED on ESP8266**

| HW-478 Pin | Connects to ESP8266 | GPIO Number (for WLED) |
|------------|----------------------|-------------------------|
| R          | D5                   | 14                      |
| G          | D6                   | 12                      |
| B          | D7                   | 13                      |
| GND        | GND                  | —                       |



## WLED App for ios and Android


- For Android [Source](https://github.com/Moustachauve/WLED-Native-Android)

- For iOS [Source](https://github.com/Moustachauve/WLED-Native-iOS/)