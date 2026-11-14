# Serial WAN Basics

> **Supplementary:** useful networking knowledge beyond the main CCNA v1.1 configuration objectives.

Legacy serial WAN labs use point-to-point serial interfaces and a Layer 2 framing protocol such as HDLC or PPP. In modern networks, Ethernet and fibre-based WAN handoffs are far more common.

## Key commands (legacy lab)
```cisco
interface serial2/0
 ip address 10.0.0.1 255.255.255.252
 encapsulation hdlc
 bandwidth 64
 clock rate 64000
 no shutdown
```

**Only configure `clock rate` on the DCE side** of the lab serial cable (check `show controllers serial 2/0`). The `bandwidth` command is a routing/management reference value; it does not physically set the serial clock speed.

## Verify
```cisco
show controllers serial 2/0
show interfaces serial 2/0
show ip interface brief
```

## Related
[Lab - Serial WAN and ACLs](25%20-%20Lab%20-%20Serial%20WAN%20and%20ACLs.md) · [Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md)

---

## Practise this topic

- [Lab - Serial WAN and ACLs](25%20-%20Lab%20-%20Serial%20WAN%20and%20ACLs.md)

---
[← Previous: 23 - Lab - Multi-Area OSPF](23%20-%20Lab%20-%20Multi-Area%20OSPF.md) · [Next: 25 - Lab - Serial WAN and ACLs →](25%20-%20Lab%20-%20Serial%20WAN%20and%20ACLs.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
