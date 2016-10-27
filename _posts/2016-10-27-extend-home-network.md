---
layout: post
title: Extend a Home Network Using a Spare Router
---

# Introduction
Extending a home network can be achieved with devices such as [Google's OnHub](https://on.google.com/hub/) or [Apple's Airport Express](http://www.apple.com/airport-express/). However, you can quickly extend your home network with a spare consumer router and a few minutes work.

# Extend Network
A standard consumer router is essentially multiple devices baked into one. It is not only a router, but a DHCP server, wireless access point and a switch. With a little bit of configuration, we will set the device up to act as just a switch and wireless access point. To achieve this you will need a wired connection from your base router to the secondary device.

## Configure Device
You must configure the device before you connect to the network.

### Access
1. Connect the device (from a LAN port) directly to your computer.
2. Access the device in a browser using it's default IP address (you should be able to find this on the back of the device). It should look something like `192.168.0.1`.
3. Enter the username and password to access the device. Again, this should be printed on the back. If not, you should be able to quickly find the default by [Googling](http://www.google.com) the devices make and model number.

### DHCP
Your base router will provide DHCP services. The role of DHCP is to assign IP addresses to devices which connect to your router. You will need to turn off DHCP on the new device. You can find DHCP settings under a dedicated tab, or on some routers it may be included under the LAN settings. Once you find the settings, disable DHCP and save.

### Wireless LAN
We can configure the new device to have the save wireless settings as the base router. This will allow modern devices to automatically change the router they communicate with as you move from one room to another. Find the wireless settings, which are generally on their own tab.

- Set the same SSID as your base router
- Set the same security type (please [don't use](http://security.stackexchange.com/questions/79187/what-is-the-best-home-wireless-network-encryption-algorithm-to-use) WEP and consider not using WPA).
- Set the channel. You can leave this option on automatic. If you wish to change it (for WiFi versions a,b,g,n), make sure the channels on your routers are at least 5 apart (e.g. 1,6 and 11) to prevent interference. The diagram below (credit [ExtremeTech](http://www.extremetech.com/computing/179344-how-to-boost-your-wifi-speed-by-choosing-the-right-channel)) demonstrates the channel overlap between 2.4 and 2.5GHz, where each channel is 22MHz wide.

![2.4GHz Bands](/resources/2016-10-27/2.4GHz-ABGN-WLAN.png)

## Connect to Network
Configuration is now complete. To being the device online, insert an ethernet cable from your base router into one of its LAN (careful, do not use the WAN port) port. You should now be able to communicate using the new device via both wired (through the remaining LAN ports) and wireless devices.
