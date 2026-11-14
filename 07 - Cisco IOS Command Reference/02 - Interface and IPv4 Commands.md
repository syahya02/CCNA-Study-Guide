# Interface and IPv4 Commands

```cisco
conf t
interface gigabitEthernet0/0
 description LAN_TO_SWITCH
 ip address 192.168.10.1 255.255.255.0
 no shutdown
exit
interface loopback 0
 ip address 10.1.1.1 255.0.0.0
end
```

| Command | Meaning |
|---|---|
| `ip address A.B.C.D MASK` | Assign IPv4 address/mask |
| `no ip address` | Clear interface IPv4 address |
| `shutdown` / `no shutdown` | Disable/enable interface |
| `description TEXT` | Document purpose |
| `interface loopback 0` | Create virtual interface |
| `show ip interface brief` | Address/link status |
| `show interfaces g0/0` | Media/counters/errors |
| `show ip arp` | ARP entries |

## IPv6
```cisco
ipv6 unicast-routing
interface g0/0
 ipv6 address 2001:db8:1::1/64
show ipv6 interface brief
show ipv6 route
```

## Related
[IPv4 Addressing](../01%20-%20Network%20Fundamentals/11%20-%20IPv4%20Addressing.md) · [IPv6 Addressing](../01%20-%20Network%20Fundamentals/16%20-%20IPv6%20Addressing.md) · [Lab - Basic Router Interfaces](../01%20-%20Network%20Fundamentals/15%20-%20Lab%20-%20Basic%20Router%20Interfaces.md)

---

[← Main study guide](../README.md)

---
[← Previous: 01 - Cisco IOS Command Reference](01%20-%20Cisco%20IOS%20Command%20Reference.md) · [Next: 03 - Switching Commands →](03%20-%20Switching%20Commands.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
