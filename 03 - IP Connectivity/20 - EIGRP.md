# EIGRP

> **Supplementary:** useful networking knowledge beyond the main CCNA v1.1 configuration objectives.

**Enhanced Interior Gateway Routing Protocol (EIGRP)** is an advanced distance-vector IGP. It uses **DUAL** to find loop-free best paths; traditional metrics combine bandwidth and delay. IP protocol number **88** (not TCP/UDP port 88).

## Classic IOS example
```cisco
router eigrp 100
 network 1.0.0.0
 network 50.0.0.0
 no auto-summary
```

The AS number must match between neighbors using classic EIGRP. EIGRP uses multicast `224.0.0.10` for IPv4 updates where applicable.

**Administrative distance:** internal = 90; external = 170. In the route table, EIGRP appears as `D`.

## Verify
```cisco
show ip eigrp neighbors
show ip eigrp topology
show ip route eigrp
show ip protocols
```

> **Training scope:** EIGRP appeared in the practical course, but is supplementary relative to the main 200-301 v1.1 exam's OSPF focus.

## Related
[Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md) · [Lab - EIGRP Routing](21%20-%20Lab%20-%20EIGRP%20Routing.md) · [OSPF](10%20-%20OSPF.md)

---

## Practise this topic

- [Lab - EIGRP Routing](21%20-%20Lab%20-%20EIGRP%20Routing.md)

---
[← Previous: 19 - Lab - RIP Across VLAN Switch Links](19%20-%20Lab%20-%20RIP%20Across%20VLAN%20Switch%20Links.md) · [Next: 21 - Lab - EIGRP Routing →](21%20-%20Lab%20-%20EIGRP%20Routing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
