## Router settings

> This is for windows!

**static IP address**

check the information of your static IP address by the following steps:


1. win+R type ncpa.cpl
2. right click ```<yourEthernet>``` properties
3. double click Internet Protocol Version 4 (TCP/IPv4) 

Copy all the information of the IP address here, set it to automatically obtain IP address afterwards.

**Router**

1. set up your router with your static IP address

2. assign a specific IP for your device from DHCP IP reservation\
   (routers assign dynamic IP addresses for devices by default, setting a specific IP address is necessary for port fowarding)

3. set up a specific port for your device's IP from NAT/port fowarding setting\
   (the specific IP above, use the same port for external and internal port just for simplicity)

Now ```<staticIPaddress>:<specificPort>``` should connect to your device, where ```<staticIPaddress>``` is the connection to your router and ```<specificPort>``` is the connection from your router to your device. 

Remember to change your device to automatically obtain IP address from where you check the IP information.