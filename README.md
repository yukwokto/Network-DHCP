# Network-DHCP Project

This repository contains configurations and instructions to set up a DHCP Server and a DHCP Relay Agent using Cisco Packet Tracer.

### Network Topology

![Network Topology](https://github.com/yukwokto/Network-DHCP/blob/a2afd978e02360ea987e54b1b1a0be40e01e3ab6/pictures/network_topology.png)

## Router as a DHCP Server

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
![show ip dhcp pool]()

