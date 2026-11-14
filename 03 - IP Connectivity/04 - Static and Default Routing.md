# Static and Default Routing

A **static route** tells a router where to send packets for a remote prefix; unlike OSPF or RIP, it is entered manually.

## IPv4 syntax
```cisco
ip route <destination-network> <subnet-mask> <next-hop-ip>
```

Example:
```cisco
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

Default route: send traffic without a more specific match toward a gateway:
```cisco
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

On Ethernet, next-hop IP addressing is often preferable to pointing a static default route only at an outbound Ethernet interface, as that may lead to extra ARP behavior.

## Common mistake
`172.16.1.0 255.255.0.0` is not aligned to /16; use `172.16.0.0/16` or `172.16.1.0/24` as appropriate.

## Verify
```cisco
show ip route
show ip interface brief
ping 10.0.0.2
traceroute 192.168.2.10
```

Check routes in **both directions**; successful outbound forwarding is not enough without a return route.

## Related
[Subnetting CIDR and VLSM](../01%20-%20Network%20Fundamentals/13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md) · [Lab - Static Routes and Loopbacks](05%20-%20Lab%20-%20Static%20Routes%20and%20Loopbacks.md) · [Lab - Default Routes](07%20-%20Lab%20-%20Default%20Routes.md)

---

## Practise this topic

- [Lab - Static Routes and Loopbacks](05%20-%20Lab%20-%20Static%20Routes%20and%20Loopbacks.md)
- [Lab - Static Routing Across VLAN Links](06%20-%20Lab%20-%20Static%20Routing%20Across%20VLAN%20Links.md)
- [Lab - Default Routes](07%20-%20Lab%20-%20Default%20Routes.md)
- [Lab - IPv6 Static Routes](08%20-%20Lab%20-%20IPv6%20Static%20Routes.md)

---
[← Previous: 03 - Routing Decisions and Longest Prefix Match](03%20-%20Routing%20Decisions%20and%20Longest%20Prefix%20Match.md) · [Next: 05 - Lab - Static Routes and Loopbacks →](05%20-%20Lab%20-%20Static%20Routes%20and%20Loopbacks.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
