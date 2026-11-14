# Lab - IPv6 Interface Basics

> **Core CCNA lab** · **Platform:** Packet Tracer · **Status:** Instructions not simulator-verified.

## Objective
Configure IPv6 addresses on one router and verify local IPv6 reachability.

## Topology and addresses
```text
PC1 --- R1 G0/0/0 --- R1 G0/0/1 --- PC2
```
| Device | IPv6 | Gateway |
|---|---|---|
| R1 G0/0/0 | `2001:db8:10::1/64` | — |
| R1 G0/0/1 | `2001:db8:20::1/64` | — |
| PC1 | `2001:db8:10::10/64` | `2001:db8:10::1` |
| PC2 | `2001:db8:20::20/64` | `2001:db8:20::1` |

## Configuration (R1)
```cisco
enable
configure terminal
hostname R1
ipv6 unicast-routing
interface gigabitEthernet0/0/0
 ipv6 address 2001:db8:10::1/64
 no shutdown
exit
interface gigabitEthernet0/0/1
 ipv6 address 2001:db8:20::1/64
 no shutdown
exit
end
write memory
```

## Configure PCs
Packet Tracer PC → Desktop → IP Configuration → IPv6; set the values above. The documentation prefix `2001:db8::/32` is meant for examples.

## Verify
```cisco
show ipv6 interface brief
show ipv6 route
show ipv6 neighbors
```
From PC1: `ping 2001:db8:20::20`.

## Troubleshoot
Confirm both interfaces are `up/up`, `ipv6 unicast-routing` is enabled, and each PC uses its local router interface as gateway.

## Lesson learned
IPv6 routing uses prefix lengths, not IPv4-style dotted subnet masks.

---
[← Previous: 16 - IPv6 Addressing](16%20-%20IPv6%20Addressing.md) · [Next: 18 - Wireless Principles →](18%20-%20Wireless%20Principles.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
