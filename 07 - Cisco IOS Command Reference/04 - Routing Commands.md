# Routing Commands

## Static / default
```cisco
ip route 192.168.2.0 255.255.255.0 10.0.0.2
ip route 0.0.0.0 0.0.0.0 10.0.0.2
ipv6 route 2001:db8:2::/64 2001:db8:12::2
```

## RIPv2
```cisco
router rip
 version 2
 no auto-summary
 network 10.0.0.0
```

## OSPF
```cisco
router ospf 1
 network 192.168.10.0 0.0.0.255 area 0
! exact-interface matching:
 network 1.1.1.1 0.0.0.0 area 0
```

## EIGRP (classic)
```cisco
router eigrp 100
 no auto-summary
 network 10.0.0.0
```

## Verify
```cisco
show ip route
show ip protocols
show ip route ospf
show ip ospf neighbor
show ip eigrp neighbors
show ipv6 route
```

## Related
[Static and Default Routing](../03%20-%20IP%20Connectivity/04%20-%20Static%20and%20Default%20Routing.md) · [RIPv2](../03%20-%20IP%20Connectivity/17%20-%20RIPv2.md) · [OSPF](../03%20-%20IP%20Connectivity/10%20-%20OSPF.md) · [EIGRP](../03%20-%20IP%20Connectivity/20%20-%20EIGRP.md)

---

[← Main study guide](../README.md)

---
[← Previous: 03 - Switching Commands](03%20-%20Switching%20Commands.md) · [Next: 05 - NAT ACL and VPN Commands →](05%20-%20NAT%20ACL%20and%20VPN%20Commands.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
