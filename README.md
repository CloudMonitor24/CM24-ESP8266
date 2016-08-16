# About CloudMonitor24

CloudMonitor24 is an Internet of Things platform that acts as a Cloud platform for any smart object or plant.
With CloudMonitor24 IoT platform you can:

* Collect measure and create historical reports 
* Monitor your smart object and being notified with email, SMS or push notifications
* Send remote commands to your smart object from everywhere

You can sign up for a free account at any time following [this link](http://www.cloudmonitor24.com/en/iot/signup)

For further information about CloudMonitor24: [www.cloudmonitor24.com/iot/](http://www.cloudmonitor24.com/en/iot/)

# Introduction

This repository contains a binary firmware for any ESP8266 device. This custom firmware has the goal to create a full IoT solution based on a standalone ESP8266 board, without writing any single line of software code. Loading this firmware to your ESP8266 board allows you to start logging data and remotely control all ESP8266 GPIOs using CloudMonitor24 platform.

# Flashing firmware

You can use esptool.py for flashing your ESP8266 based board. This is an example of how to use esptool.py:

```
./esptool.py --port /dev/ttyS0 write_flash 0x00000 ./bin/eagle.flash.bin 0x28000 ./bin/eagle.irom0text.bin 0x7C000 ./bin/esp_init_data_default.bin 0x7E000 ./bin/blank.bin
```

Please refer to address specified on example above in order to know where firmware should be placed in flash memory.
Firmware has been fully tested on ESP-12 amd NodeMCU modules. In general, any ESP8266 device with at least 1 Mb of flash memory should be supported without any restriction.

# Initial setup

After CM24-ESP8266 firmware has been loaded into your board, just power on the device. Due to the fact ESP8266 doesn't find a valid configuration, it will start in AP mode, creating it's own WiFi network. Connect your PC to this network (using DHCP and not a static IP address):

```
SSID: CloudMonitor24-<ESP8266_MAC_ADDRESS>
Password: testcm24
```

Then open any modern browser and connect to your ESP8266 board. You'll find web interface at this address, accessible with these standard credentials: 

```
Address: http://192.168.1.1
Username: admin
Default password: 12345
```

Using web interface you can apply all settings required to connect to your own WiFi network, connect to CloudMonitor24 platform and set all ESP8266 GPIOs and analog input.
Once configuration is done, just save it and restart board. At the next boot, ESP8266 will find a valid configuration and it will try to use your own WiFi network to connect to CloudMonitor24 platform.
In case of wrong WiFi settings, after 1 minute ESP8266 will enter AP mode and launch its own Wifi network again.

# License

This firmware is free and distributed without any warranty for personal use. 
For commercial use please contact cloudmonitor24@imotion.it for licensing information.


