# NAT and PAT

**Network Address Translation (NAT)** rewrites IP addresses; **PAT** (overload) additionally tracks transport ports/identifiers so multiple internal hosts can share one translated IPv4 address.

## Important terms
- **Inside local**: private/internal address before translation.
- **Inside global**: translated address seen by the outside.
- **Static NAT**: fixed one-to-one mapping.
- **Dynamic NAT**: mapping from a pool.
- **PAT**: many-to-one sharing via port/identifier translation.

## Cisco PAT example
```cisco
interface g0/0
 ip nat inside
interface g0/1
 ip nat outside
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
```

## Verify
```cisco
show ip nat translations
show ip nat statistics
show access-lists
```
Generate traffic first: an empty NAT table is not proof of misconfiguration. NAT is **not** encryption or a firewall substitute.

## Related
[Lab - NAT and PAT](07%20-%20Lab%20-%20NAT%20and%20PAT.md) · [ACLs](../05%20-%20Security%20Fundamentals/04%20-%20ACLs.md) · [IPv4 Addressing](../01%20-%20Network%20Fundamentals/11%20-%20IPv4%20Addressing.md)

---
[← Previous: 04 - Lab - DHCP Server and Relay](04%20-%20Lab%20-%20DHCP%20Server%20and%20Relay.md) · [Next: 06 - NAT Types and Translation Pools →](06%20-%20NAT%20Types%20and%20Translation%20Pools.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
