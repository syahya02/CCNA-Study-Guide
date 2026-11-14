# IPv6 Addressing

IPv6 addresses are **128 bits**, represented as eight hexadecimal groups. Leading zeroes in a group may be omitted, and **one contiguous run** of zero groups can be compressed as `::` once per address.

Example: `2001:db8:1::10/64` (`2001:db8::/32` is documentation space).

## Major address types
- **Global unicast**: internet-routable addresses (commonly in `2000::/3`).
- **Link-local**: `fe80::/10`; needed for neighboring communication and many IPv6 routing operations.
- **Unique local**: `fc00::/7`; private-scope design.
- **Multicast**: `ff00::/8`; IPv6 has **no broadcast**.
- **Loopback**: `::1`; unspecified: `::`.

## Address configuration on Cisco IOS

```cisco
conf t
ipv6 unicast-routing
interface g0/0
 ipv6 address 2001:db8:1::1/64
 no shutdown
end
show ipv6 interface brief
show ipv6 route
```

Clients may use SLAAC or DHCPv6 (where configured); Neighbor Discovery replaces several IPv4 ARP functions.

## Related
[Lab - IPv6 Static Routes](../03%20-%20IP%20Connectivity/08%20-%20Lab%20-%20IPv6%20Static%20Routes.md) · [IPv4 Addressing](11%20-%20IPv4%20Addressing.md)

---

## Practise this topic

- [Lab - IPv6 Interface Basics](17%20-%20Lab%20-%20IPv6%20Interface%20Basics.md)

## Important IPv6 address types

- **Global unicast:** routable addressing, commonly within `2000::/3`.
- **Link-local:** `fe80::/10`, used for on-link functions and as next-hop addresses.
- **Unique local:** `fc00::/7`, locally scoped addresses typically `fd00::/8`.
- **Multicast:** `ff00::/8`; IPv6 has **no broadcast**.
- **Anycast:** same unicast address assigned to several devices; routing selects an instance.
- **Modified EUI-64:** one method to create an interface identifier from a MAC, with FF:FE insertion and U/L bit inversion; privacy-address methods are also common.

---
[← Previous: 15 - Lab - Basic Router Interfaces](15%20-%20Lab%20-%20Basic%20Router%20Interfaces.md) · [Next: 17 - Lab - IPv6 Interface Basics →](17%20-%20Lab%20-%20IPv6%20Interface%20Basics.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
