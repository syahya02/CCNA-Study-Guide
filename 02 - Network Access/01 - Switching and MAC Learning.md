# Switching and MAC Learning

A Layer 2 switch builds a **MAC address table** by recording the **source MAC**, VLAN and incoming switchport of received frames.

- **Known unicast**: forward only out the learned destination port (if allowed).
- **Unknown unicast**: flood eligible ports in the VLAN except the ingress port.
- **Broadcast**: flood within the VLAN; routers separate VLAN broadcast domains.
- Entries age out; hosts may move to different ports.

## Quick commands
```cisco
show mac address-table
show interfaces status
show interfaces trunk
show vlan brief
```

## ARP vs switching
ARP resolves IPv4 next-hop IP addresses to local MAC addresses. A router rewrites Ethernet frame addressing at each hop.

## Related
[Ethernet and Cabling](../01%20-%20Network%20Fundamentals/08%20-%20Ethernet%20and%20Cabling.md) · [VLANs](02%20-%20VLANs.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md)

---
[← Chapter study path](README.md) · [Next: 02 - VLANs →](02%20-%20VLANs.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
