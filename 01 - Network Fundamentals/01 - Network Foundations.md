# Network Foundations

A network links devices so they can communicate and share data, applications, printers, storage and internet access. A **LAN** covers a local area; a **WAN** joins networks across larger distances, commonly through an ISP.

## Common devices

| Device | Primary role |
|---|---|
| Router | Forwards packets between IP networks (Layer 3) |
| Layer 2 switch | Learns MAC addresses and forwards Ethernet frames within VLANs |
| Layer 3 switch | Switches frames and can route between IP subnets using SVIs or routed ports |
| Access point | Connects wireless clients to a wired network |
| Firewall | Enforces traffic policies across zones/networks |
| End hosts | PCs, servers, printers, phones and IoT devices |

## Important vocabulary

- **Bandwidth**: nominal link capacity; **throughput**: actual achieved data rate; **latency**: delay.
- **Broadcast domain**: devices that can receive a Layer 2 broadcast; a VLAN normally defines one.
- **Collision domain**: a segment where Ethernet collisions can occur; switched full-duplex links avoid shared-media collisions.
- **Default gateway**: the local router interface used to reach other IP networks.

## Related
[OSI Model](05%20-%20OSI%20Model.md) · [Ethernet and Cabling](08%20-%20Ethernet%20and%20Cabling.md) · [VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [Routing Table and Administrative Distance](../03%20-%20IP%20Connectivity/02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---
[← Chapter study path](README.md) · [Next: 02 - Network Devices →](02%20-%20Network%20Devices.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
