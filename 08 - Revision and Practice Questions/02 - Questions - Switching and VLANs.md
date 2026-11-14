# Questions - Switching and VLANs

**1. What is a VLAN?**
A logical Layer 2 broadcast domain.

**2. Access vs trunk port?**
Access belongs to one VLAN; trunk carries multiple VLANs using 802.1Q tagging.

**3. Does a trunk route between VLANs?**
No. A router or Layer 3 switch must route between different IP networks.

**4. What is router-on-a-stick?**
One physical router interface with VLAN-tagged subinterfaces provides gateways for several VLANs.

**5. What is an SVI?**
A switched virtual Layer 3 interface (`interface vlan X`) often serving as VLAN gateway.

**6. Why did R1-to-R2 fail after changing SW2 router access port to VLAN 20?**
Their Layer 2 ports were in different VLANs and the trunk did not translate VLANs.

**7. What does 802.1Q do?**
Carries VLAN identification in tagged Ethernet frames.

**8. What does VTP distribute?**
VLAN database information, not SVI addresses or inter-VLAN routes.

**9. What problem does STP prevent?**
Bridging loops, duplicate frames, broadcast storms.

**10. What does LACP provide?**
Negotiation/maintenance of bundled physical ports in an EtherChannel.

## Review
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [Trunking and 802.1Q](../02%20-%20Network%20Access/03%20-%20Trunking%20and%20802.1Q.md) · [STP and EtherChannel](../02%20-%20Network%20Access/11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md)

---

[← Main study guide](../README.md)

---
[← Previous: 01 - Questions - Fundamentals and IP](01%20-%20Questions%20-%20Fundamentals%20and%20IP.md) · [Next: 03 - Questions - Routing →](03%20-%20Questions%20-%20Routing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
