﻿# BSD29
## Product Details
![Overview](https://github.com/chris173972/my-tuya-devices-conversion/blob/main/wifi_plugs/BSD29/BSD29_Overall.jpg?raw=true)
![Overview](https://github.com/chris173972/my-tuya-devices-conversion/blob/main/wifi_plugs/BSD29/BSD29_Inside.jpg?raw=true)
![Overview](https://github.com/chris173972/my-tuya-devices-conversion/blob/main/wifi_plugs/BSD29/BSD29_Details.jpg?raw=true)

## Project Used 
- tuya-cloudcutter: https://github.com/tuya-cloudcutter/tuya-cloudcutter
- ESPHome - https://esphome.io/
- Home Assistant -  https://www.home-assistant.io/

## Hardware Used
- Hardware: Raspberry Pi 4 (https://github.com/tuya-cloudcutter/tuya-cloudcutter/blob/main/HOST_SPECIFIC_INSTRUCTIONS.md)
- OS: Raspberry OS
- Docker Installed
- Do not connect to network via wifi. Use Ethernet to keep Wifi free for the process

## Process - Do this at your own risk
**Smartlife**
- Check device firmware version within app: 1.1.7

**Terminal**:
- Make sure you know this process is only one way so once done, this will no longer communicate with Tuya
- git clone https://github.com/tuya-cloudcutter/tuya-cloudcutter
- cd tuya-cloudcutter
- sudo ./tuya-cloudcutter.sh
- Select: 2 - Flash 3rd Party Firmware
- Select: By firmware version and name
- Select: 1.1.7 - BK7231N / oem_bk7231n_plug
- Select: ESPHome-Kickstart-v23.08.29_bk7231n_app.ota.ug.bin
- Put device into AP mode: press hold button untill fast flash, press and hold again till slow flash
- Will show the device is connected on termainal
- Unplug the device and plug back in.
- Put device into AP mode again: press hold button untill fast flash, press and hold again till slow flash
- Please be patient. May take a while based upon machine used
- Will show device mac address if success.

**Compile ESPHome Firmware**
- Navigate to installed ESPHome: https://esphome.io/guides/getting_started_hassio
- Select: New device
- Select: Continue
- Name your device -> Next
- Select BK72xx
- Select CB2S Wi-Fi Module -> Next
- Select Skip (we will be updating these details on yaml)
- Edit device created
- Copy contents of: BSD29.yaml: https://github.com/chris173972/my-tuya-devices-conversion/blob/main/wifi_plugs/BSD29/BSD29.yaml 
- Select: Install
- Select: Manual download
- Please be patient. May take a while based upon machine used
- Select: UF2 package (recommended)

**Update device with ESPHome Firmware**
- Connect computer to hotspot: 'kickstart-????' (specific to your device)
- Open web browser to: 192.168.4.1
- Select Select Update -> Select firmware you downloaded from ESPHome
- Select Update
- Please be patient for the device to update

**Connect to Home Assistant**
- Open home assistant
- Device should be detected within integrations 'add new device'
- If not, select ESPHome, Add device

**Star the project at https://github.com/tuya-cloudcutter/tuya-cloudcutter**
