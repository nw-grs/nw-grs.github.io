# ASA NAT

## Configuring Dynamic NAT

*  NAT can be configured in two ways
    + Manual NAT (Configured Globally)
    + Auto NAT (Configured under the object)
* Manual NAT comes in Section 1 or Section 3. Default is Section 1
* Auto NAT comes in Section 2
* The order in which NAT is checked
    + Section 1 is checked first, top-down
    + If no match in Section 1, it moves to Section 2
    + In Section 2, again rules are checked top-down
    + If no matches in Section 2, it moves to Section 3
    + If no match in Section 3, the traffic is untranslated
* Section 1 wins over Section 2
* Within a Section it's the sequence number which takes preference.
* If a NAT rule matches then it needs to be translated. Else, it would be dropped. So, if there is no pool or free IP available, traffic gets dropped.
* In ASA code 9.6, access-list hits after NAT when request comes from lower security-level destined to higher security-level. So, we would always need private IP address as destination and private port as destination port.

---

* Dynamic NAT translates a group of real addresses to a pool of mapped addresses that are routable on the destination network
* Dynamic NAT is uni-directional. (Only the source IP address is translated)
* Dynamic NAT

```
object network OBJECT-REAL
 subnet 192.168.65.0 255.255.255.0
object network OBJECT-MAPPED
 range 74.0.0.150 74.0.0.160

nat (INSIDE,OUTSIDE) source dynamic OBJECT-REAL OBJECT-MAPPED

ASAx1(config)# sh nat
Manual NAT Policies (Section 1)
1 (INSIDE) to (OUTSIDE) source dynamic OBJECT-REAL OBJECT-MAPPED
    translate hits = 0, untranslate hits = 0
```


---

[🔙 Back](../README.md)
