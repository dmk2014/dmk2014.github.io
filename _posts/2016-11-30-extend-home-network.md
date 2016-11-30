---
layout: post
title: Extend a Home Network with a Spare Router
---

# Introduction
Extending a home network can be achieved with devices such as [Google's OnHub](https://on.google.com/hub/) or [Apple's Airport Express](http://www.apple.com/airport-express/). However, a home network be extended with a spare consumer router and a few minutes work.

# Extend Network
A standard consumer router consists of multiple devices baked into one. It is not only a router, but a DHCP server, wireless access point and a network switch. With a little bit of configuration, the device can be configured to function as just as a switch and wireless access point. To achieve this a wired connection is required from the base router to the secondary device.

## Configure Device
The device must be configured before connecting it to the existing network.

### Access Configuration Webpage
1. Connect the device (from a LAN port) directly to a computer.
2. Access the device in a browser using it's default IP address. This is normally printed on the back of the device and will look something like `192.168.0.1`.
3. Enter the username and password to access the device. Again, this will normally be printed on the back. If not, the default credentials can usually be found by [Googling](http://www.google.com) the make and model number of the device.

### DHCP
The base router will provide DHCP services. The role of DHCP is to assign IP addresses to devices which connect to the router. It must be turned off on the secondary device. DHCP settings may be found under a dedicated tab, though on some models it can be included under the LAN settings. Disable DHCP and save.

### Wireless LAN (WLAN)
The secondary device can be configured with the same WLAN settings as the base router. This will allow modern devices to automatically choose which router they communicate through based on factors such as signal strength. WLAN settings are generally located on their own tab.

1. Set the same SSID as the base router.
2. Set the same security type ([don't use](http://security.stackexchange.com/questions/79187/what-is-the-best-home-wireless-network-encryption-algorithm-to-use) WEP and consider not using WPA).
3. Set the channel. This option can be set to automatic. When using a specific value (for WiFi versions a, b, g and n), ensure that the channels on the routers are at least 5 apart (e.g. 1,6 and 11) to prevent interference. The diagram below (credit [ExtremeTech](http://www.extremetech.com/computing/179344-how-to-boost-your-wifi-speed-by-choosing-the-right-channel)) demonstrates the channel overlap between 2.4 and 2.5GHz, where each channel is 22MHz wide.

![2.4GHz Bands](/resources/2016-11-30/2.4GHz-ABGN-WLAN.png)

## Connect to Network
Configuration is now complete. The device can be brought online be connecting it to the base router with an ethernet cable. Ensure to connect via one of its LAN ports. Network access can now be achieved using both wired (through the remaining LAN ports) and wireless connections.
