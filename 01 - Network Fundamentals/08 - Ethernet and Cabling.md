# Ethernet and Cabling

**Ethernet** defines local-network framing and link characteristics. A switch learns source MAC addresses on ingress ports and forwards unicast frames toward known destinations; unknown unicasts and broadcasts may be flooded within the VLAN.

## Media
- **Copper UTP**: RJ-45 connections in many LANs, distance and speed depend on cable category and standard.
- **Multimode fibre**: common shorter optical runs.
- **Single-mode fibre**: common longer optical links.
- **Full duplex**: send/receive concurrently; conventional CSMA/CD collisions are absent.

## Ethernet basics

- Broadcast destination MAC: `FF:FF:FF:FF:FF:FF`.
- A VLAN usually separates broadcast domains.
- **802.1Q** adds a VLAN tag on trunk links, typically except native-VLAN traffic by default.
- Auto-MDI/MDIX usually removes the old practical need to pick straight-through versus crossover cables.

## Troubleshoot
```cisco
show interfaces status
show interfaces gigabitEthernet0/1
show mac address-table
```
Check cable, link status, duplex/speed mismatch, CRC errors and interface counters.

## Related
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [Trunking and 802.1Q](../02%20-%20Network%20Access/03%20-%20Trunking%20and%20802.1Q.md) · [Switching and MAC Learning](../02%20-%20Network%20Access/01%20-%20Switching%20and%20MAC%20Learning.md)

---
[← Previous: 07 - Unicast Broadcast and Multicast](07%20-%20Unicast%20Broadcast%20and%20Multicast.md) · [Next: 09 - Interface and Cable Troubleshooting →](09%20-%20Interface%20and%20Cable%20Troubleshooting.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
