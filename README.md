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

#Hostname of Machine
echo "Enter Hostname"
read host
cp /etc/hosts /etc/hosts_bkp

echo "$ip server.$host server" >> /etc/hosts

cp /etc/resolv.conf /etc/resolv.conf_bkp
echo "search $host
nameserver $ip" >> /etc/resolv.conf

cp /etc/sysconfig/network /etc/sysconfig/network_bkp
echo "NETWORKING=yes
HOSTNAME=$host" >> /etc/sysconfig/network

#*************Script End*************

service network restart

