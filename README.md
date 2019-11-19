#!/bin/bash
echo "########******Start Script******#######"
cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth0-bkp
echo "Enter IP adderss "
read ip
echo "Enter Broadcast "
read broadc
echo "Enter Netmask"
read netmask
echo "Enter Gateway"
read gateway
echo "Enter Network"
read network

echo "DEVICE=eth0
BOOTPROTO=static
TYPE=Ethernet
BROADCAST=$broadc
IPADDR=$ip
NETMASK=$netmask
NETWORK=$network
GATEWAY=$gateway
ONBOOT=yes
ARPCHECK=no" > /etc/sysconfig/network-scripts/ifcfg-eth0

