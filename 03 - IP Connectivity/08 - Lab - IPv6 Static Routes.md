# Lab - IPv6 Static Routes

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Connect two IPv6 LANs over one inter-router link using IPv6 static routes.

## Topology

```text
PC1 --- R1 ===== R2 --- PC2
```

## Addressing / prerequisites
LAN1 `2001:db8:1::/64`; WAN `2001:db8:12::/64`; LAN2 `2001:db8:2::/64`. PC1 `2001:db8:1::10/64` gw `2001:db8:1::1`; PC2 `2001:db8:2::10/64` gw `2001:db8:2::1`. IPv6 `2001:db8::/32` is documentation-only.

## Configuration

### R1

```cisco
enable
conf t
hostname R1
ipv6 unicast-routing
interface g0/0
 description LAN_1
 ipv6 address 2001:DB8:1::1/64
 no shutdown
interface g0/1
 description WAN_TO_R2
 ipv6 address 2001:DB8:12::1/64
 no shutdown
exit
ipv6 route 2001:DB8:2::/64 2001:DB8:12::2
end
wr
```

### R2

```cisco
enable
conf t
hostname R2
ipv6 unicast-routing
interface g0/0
 description LAN_2
 ipv6 address 2001:DB8:2::1/64
 no shutdown
interface g0/1
 description WAN_TO_R1
 ipv6 address 2001:DB8:12::2/64
 no shutdown
exit
ipv6 route 2001:DB8:1::/64 2001:DB8:12::1
end
wr
```

## Verify

```cisco
show ipv6 interface brief
show ipv6 route
show ipv6 neighbors
ping 2001:DB8:12::2
```

## Troubleshooting and expected result
Ping `2001:db8:2::10` from PC1. Ensure both PCs have correct IPv6 gateways and IPv6 forwarding is enabled on the routers.

## Related notes
[IPv6 Addressing](../01%20-%20Network%20Fundamentals/16%20-%20IPv6%20Addressing.md) · [Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md)

---
[← Previous: 07 - Lab - Default Routes](07%20-%20Lab%20-%20Default%20Routes.md) · [Next: 09 - Static Route Variants →](09%20-%20Static%20Route%20Variants.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
