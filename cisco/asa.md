# ASA Firewall

## Table of Content

* Configuring IP Addressing on ASA
* Defining nameif and security levels on ASA
* Configuring Management access on ASA
* Understanding ACL's on ASA
* NAT on ASA
* Deep Inspection on ASA
* Transparent Firewall
* Multi-Context
* Active/Standby Failover
* Active/Active Failover
* Clustering Individual Versus Spaned


## Defining nameif and security levels on ASA

### Configuring IP Addressing on ASA

```
> enable
# show interface ip brief
```

```
# configure terminal
(config)# interface g0/0
(config-if)# ip address 10.0.0.1 255.255.255.0
(config-if)# no shut
```

### Nameif Considerations

Every interface must have *nameif* defined. It must be unique on every interface, and is is also case-sensitive.

### Security levels on the firewall

* Allows the firewall to pass traffic from trusted network to untrusted network.
* Deny's traffic from untrusted network to trusted network by default, without an ACL.
* Ranges from 0 to 100. 0 being the lowest and 100 being the highest.
* Always assign the security level 100 to the interface facing the trusted network.
* Always assign the security level 0 to the interface facing the untrusted network.


## Routing Protocols
---

[🔙 Back](../README.md)