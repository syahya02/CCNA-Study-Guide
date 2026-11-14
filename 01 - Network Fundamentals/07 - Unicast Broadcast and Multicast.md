# Unicast Broadcast and Multicast

| Type | Meaning | Example |
|---|---|---|
| Unicast | One sender to one receiver | SSH to a specific router |
| Broadcast | One sender to all hosts in the Layer 2 broadcast domain | ARP request on Ethernet; IPv4 limited broadcast |
| Multicast | One sender to members of a group | OSPF Hello to `224.0.0.5` (IPv4) |

IPv4 broadcast usually stays within the local broadcast domain; routers do not normally forward it. IPv6 uses multicast instead of broadcast.

## Why it matters
Switches flood broadcasts within a VLAN. Routers separate broadcast domains. ACLs, security features and multicast configuration affect what traffic is delivered.

## Related
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [IPv4 Addressing](11%20-%20IPv4%20Addressing.md) · [OSPF](../03%20-%20IP%20Connectivity/10%20-%20OSPF.md)

---
[← Previous: 06 - TCP-IP Model and Encapsulation](06%20-%20TCP-IP%20Model%20and%20Encapsulation.md) · [Next: 08 - Ethernet and Cabling →](08%20-%20Ethernet%20and%20Cabling.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
