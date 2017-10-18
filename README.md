# Cheatsheet for some configurations

configuring a bridge:

First of all I would reccomend doing this from console as you might loose connectivity in between
- apt-get install bridge-utils
- ip addr flush dev eth0
- brctl addbr mybridge
- brctl addif mybridge eth0
- ifconfig mybridge up
- ifconfig mybridge 10.84.7.32 netmask 255.255.255.0 up
- route add default gw <gateway-ip>

