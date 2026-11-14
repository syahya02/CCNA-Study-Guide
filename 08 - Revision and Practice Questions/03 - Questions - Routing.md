# Questions - Routing

**1. What is a directly connected route?**
A route installed because the router owns an up/up interface in that subnet.

**2. When does longest-prefix match apply?**
When selecting the most specific matching route for a destination.

**3. What does AD mean?**
Administrative Distance: preference between competing sources for the same prefix; lower is preferred.

**4. Default AD of static, OSPF and RIP?**
Static 1, OSPF 110, RIP 120.

**5. Why use loopbacks in routing labs?**
To simulate stable, directly connected remote networks without extra physical hardware.

**6. RIPv2 metric and max usable hop count?**
Hop count; 15 (16 = unreachable).

**7. What does `no auto-summary` do in RIP?**
Prevents automatic classful aggregation at classful boundaries.

**8. Why must OSPF area 0 exist in normal multi-area designs?**
It is the backbone through which inter-area routing is structured.

**9. What is an ABR?**
An OSPF router participating in Area 0 and one or more other areas.

**10. What wildcard matches exactly `1.1.1.1` in OSPF?**
`0.0.0.0`.

**11. What does `O IA` mean?**
OSPF inter-area route.

**12. What is a default static route?**
`0.0.0.0 0.0.0.0 NEXT_HOP`.

**13. IP protocol number for OSPF and EIGRP?**
OSPF 89; EIGRP 88 (not TCP/UDP ports).

**14. Why can a ping fail despite a valid route?**
Missing reverse route, ACL, firewall, down interface or incorrect destination configuration.

## Review
[Routing Table and Administrative Distance](../03%20-%20IP%20Connectivity/02%20-%20Routing%20Table%20and%20Administrative%20Distance.md) · [OSPF](../03%20-%20IP%20Connectivity/10%20-%20OSPF.md) · [RIPv2](../03%20-%20IP%20Connectivity/17%20-%20RIPv2.md)

---

[← Main study guide](../README.md)

---
[← Previous: 02 - Questions - Switching and VLANs](02%20-%20Questions%20-%20Switching%20and%20VLANs.md) · [Next: 04 - Questions - Services and Security →](04%20-%20Questions%20-%20Services%20and%20Security.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
