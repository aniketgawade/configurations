# Cheatsheet for some configurations

configuring a bridge:

First of all I would reccomend doing this from console as you might loose connectivity in between
- apt-get install bridge-utils
- ip addr flush dev eth0
- brctl addbr mybridge
- brctl addif mybridge eth0
- ifconfig mybridge up
- ifconfig mybridge 10.84.7.32 netmask 255.255.255.0 up
- route add default gw (gateway-ip)

Another way of doing this is

Edit /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br-mgmt
iface br-mgmt inet static
    address 10.99.99.99
    netmask 255.255.255.0
    gateway 10.99.99.254
    bridge_ports eth0

```
then

ip address flush eth0 scope global && ifup br-mgmt

