# ESP8266-fiware-gateway

FIWARE-GWAP gateway based on the ESP8266 WiFi SOC.

![GWAP sensor device and FIWARE-enabled gateway](http://www.panstamp.org/pictures/fiware_01.jpg)

## FIWARE

[FIWARE](https://www.fiware.org/) is an open source software ecosystem designed to manage massive IoT information and connect from all kind of devices and applications. The core of FIWARE is the Context-Broker, a complete IoT data manager providing a full set of API Rest primitives. Additionally, FIWARE instances can be equipped with IoT agents specially made to connect to lightweight hardware such as low-power IoT devices.

Upon reception of any HTTP request from a gateway, the UL (Ultralight) IoT agent automatically creates the device and the entity on the Context-Broker if it does not exist. Entity attributes (endpoints) are also generated by the agent. This releases us from having to provision the device resources each time. The 12-byte GWAP UID of the wireless sensor device is taken as the entity id for the Context-broker. This let us virtually handle unlimited amounts of wireless devices through a single gateway.

## RF gateway

This application relies on a panStamp NRG module for the low-power wireless communications. This module runs gwapmodem and transmits any wireless packet received to the ESP8266 via serial. After receiving the (GWAP) wireless packet from the NRG board, the ESP8266 module processes it and forwards the endpoint information to Fiware. Submissions to Fiware are done by means of the UL (UltraLight) IoT agent.

Any amount of gateways can coexist in the same network, all connected to a common FIWARE instance. This feature makes this solution specially suited for low-power wide area applications.

## GWAP

[GWAP](https://github.com/liberiot/gwap) is the protocol used between low-power wireless motes and gateways. This protocol is open, fully bi-directional and uses unique 12-byte addresses for each device. This makes each device uniquely identifiable around the globe. GWAP takes very little space in flash and RAM so it's suitable for almost any commercial MCU platform.

## WiFi

The gateway needs to connect to a secured WiFi network. WiFiManager is being used in the Arduino core so the ESP8266 will prompt the user to introduce new WiFi ssid and password from the captive portal on [http://192.168.4.1](http://192.168.4.1).

## Links

* [FIWARE.org](https://www.fiware.org/)
* [panStamp NRG - Wiki page](https://github.com/panStamp/panstamp/wiki/panStamp%20NRG%202.-Technical%20details)
* [Global Wireless Abstract Protocol (GWAP)](https://github.com/liberiot/gwap)
* [GWAP modem application](https://github.com/panStamp/panstamp_sketches/tree/master/gwapmodem)

