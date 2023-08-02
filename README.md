# Network-DHCP Project

This repository contains configurations and instructions to set up a DHCP Server and a DHCP Relay Agent using Cisco Packet Tracer.

### Network Topology

![Network Topology](https://github.com/yukwokto/Network-DHCP/blob/a2afd978e02360ea987e54b1b1a0be40e01e3ab6/pictures/network_topology.png)

## 1. Router as a DHCP Server

Basic Configuration on the Router:
```
Router>en
Router#config t
Router(config)#int g0/0/0
Router(config-if)#ip address 10.10.10.1 255.255.255.0
Router(config-if)#no shutdown
```

DHCP Configuration on the Router
```
Router(config)#ip dhcp excluded-address 10.10.10.1 10.10.10.30
Router(config)#ip dhcp pool Client_Pool
Router(dhcp-config)#network 10.10.10.0 255.255.255.0
Router(dhcp-config)#default-router 10.10.10.1
Router(dhcp-config)#dns-server 10.10.10.1
```

DHCP set-up Verification
```
show ip dhcp pool
```
![show ip dhcp pool](https://github.com/yukwokto/Network-DHCP/blob/ceeb7a92732216deafe5bb521fc7b28c0a6784ad/pictures/router_show_ip_dhcp_pool.png)

2 ip addresses have been leased (to PC0 and PC1).
```
show ip dhcp binding
```
![show ip dhcp binding](https://github.com/yukwokto/Network-DHCP/blob/81cd8f0eaac4272c61ab23d6974c3fd545060e76/pictures/router_show_ip_dhcp_binding.png)

![PC1](https://github.com/yukwokto/Network-DHCP/blob/1187fbcbd4e7849c8c7c81a754eb9968607950c1/pictures/pc1_renew.png)

![PC0](https://github.com/yukwokto/Network-DHCP/blob/1187fbcbd4e7849c8c7c81a754eb9968607950c1/pictures/pc0_renew.png)


## 2. Router as a DHCP Relay Agent

DHCP and DNS Server Configuration
![DHCP and DNS Server Configuration](https://github.com/yukwokto/Network-DHCP/blob/1c32895ba2c5f4e5e2765610337aff5f4bddd347/pictures/server_dhcp_setting.png)

Configuration on Router as a DHCP Relay Agent:
```
Router>en
Router#config t
Router(config)#int g0/0
Router(config-if)#ip address 10.10.10.1 255.255.255.0
Router(config-if)#no shutdown

Router(config)#int g0/1
Router(config-if)#ip address 10.10.20.5 255.255.255.0
Router(config-if)#no shutdown

Router(config-if)#int g0/0
Router(config-if)#ip helper-address 10.10.20.1
```

Verification:


![PC2](https://github.com/yukwokto/Network-DHCP/blob/1187fbcbd4e7849c8c7c81a754eb9968607950c1/pictures/pc2_renew.png)
![PC3](https://github.com/yukwokto/Network-DHCP/blob/1187fbcbd4e7849c8c7c81a754eb9968607950c1/pictures/pc3_renew.png)


In conclusion, this project provides a comprehensive guide to setting up a DHCP server and DHCP relay agent using Cisco Packet Tracer. The DHCP server configuration enables the router to dynamically assign IP addresses, default gateways, and DNS server settings to client devices on the LAN. On the other hand, the DHCP relay agent configuration allows the router to forward DHCP messages from clients on one network to the DHCP server on a different network. 





