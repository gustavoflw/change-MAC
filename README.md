## Methods of achieving a Wi-Fi Access Point with configurable MAC
---
### ESP controller as Access Point (TESTED)
- Change MAC
    - [Step-by-step for ESP8266 and ESP32](https://randomnerdtutorials.com/get-change-esp32-esp8266-mac-address-arduino/)
- Configure AP Web Server
    - Can ignore the web server part
    - [Step-by-step for ESP8266](https://randomnerdtutorials.com/esp8266-nodemcu-access-point-ap-web-server/)
    - [Step-by-step for ESP32](https://randomnerdtutorials.com/esp8266-nodemcu-access-point-ap-web-server/)
---
### Router with open source firmware (TESTED)
- [List of supported OpenWrt devices](https://openwrt.org/supported_devices)
- [Get OpenWrt firmware for TP-Link TL-WR841ND](https://openwrt.org/toh/tp-link/tl-wr841nd)
- Once you have the custom firmware
    - Activate SSH from the web interface
        - Router configuration page (default 192.168.1.1) --> System --> administration --> Enable SSH on LAN
    - Access router with SSH and edit wireless file
        - ``ssh admin@192.168.1.1``
    - Edit wireless file
        - ``nano /etc/config/wireless``
    - In section "wifi-iface", insert your custom MAC:
        - ``option macaddr 00:11:22:33:44:55``
    - Reboot the router
        - ``reboot``
---
### Linux PC working as router (UNTESTED)
- Your NIC needs to support configurable MAC
- macchanger
    - Install
        - ``sudo apt install macchanger``
    - How to use
        - ``sudo macchanger -m 00:11:22:33:44:55 wlan0``
- hostapd
    - Install
        - ``sudo apt install hostapd``
    - Configure network
---