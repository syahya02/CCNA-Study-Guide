# Routing Table and Administrative Distance

A router forwards traffic using the **best matching route** in its forwarding table. **Longest prefix match** is checked first; when competing route sources advertise the **same prefix**, administrative distance (AD) helps choose which source is installed. A routing protocol's metric is then relevant when comparing routes learned by that protocol.

## Cisco route codes
| Code | Meaning |
|---|---|
| C | Connected network |
| L | Local interface address (/32) |
| S | Static route |
| R | RIP |
| D | EIGRP (internal) |
| O | OSPF intra-area |
| O IA | OSPF inter-area |

## Default administrative distances
| Source | AD |
|---|---:|
| Connected | 0 |
| Static | 1 |
| eBGP | 20 |
| EIGRP internal | 90 |
| OSPF | 110 |
| RIP | 120 |
| EIGRP external | 170 |
| iBGP | 200 |
| Unusable / unknown | 255 |

**Example:** for the *same* `192.168.50.0/24` prefix, a normal OSPF route (AD 110) beats a RIP route (AD 120). But a more-specific `/25` route can win traffic for its addresses regardless of another route's AD due to longest-prefix matching.

## Commands
```cisco
show ip route
show ip route 192.168.50.0
show ip protocols
```

## Related
[Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md) · [RIPv2](17%20-%20RIPv2.md) · [OSPF](10%20-%20OSPF.md) · [EIGRP](20%20-%20EIGRP.md)

---
[← Previous: 01 - Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Next: 03 - Routing Decisions and Longest Prefix Match →](03%20-%20Routing%20Decisions%20and%20Longest%20Prefix%20Match.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
