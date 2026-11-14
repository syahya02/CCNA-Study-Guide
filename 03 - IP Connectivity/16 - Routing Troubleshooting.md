# Routing Troubleshooting

## Check systematically

1. **Link**: `show ip interface brief` (up/up?)
2. **Address**: correct subnet/mask on both ends?
3. **Next hop**: ping directly connected neighbor.
4. **Routing**: `show ip route` has destination, and remote router has return route?
5. **Protocol**: `show ip protocols`, OSPF/EIGRP neighbors, ACLs filtering traffic?
6. **End host**: correct default gateway, host firewall, VLAN access-port membership?

## Commands
```cisco
show ip interface brief
show ip route
show ip protocols
show cdp neighbors
ping 192.168.10.1
traceroute 192.168.10.10
```

## Common lab errors
- Applying a crypto map to `g0/1` instead of the actual `g0/0/1`.
- Assigning one end of an Ethernet bridge to VLAN 10 and the other to VLAN 20.
- OSPF area mismatch/wrong wildcard or missing backbone design.
- Mistyping a /16 network address in a static route.
- Forgetting `no shutdown` or a PC default gateway.

## Related
[Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md) · [OSPF](10%20-%20OSPF.md) · [VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [Lab - Multi-Area OSPF](23%20-%20Lab%20-%20Multi-Area%20OSPF.md)

---
[← Previous: 15 - Lab - HSRP Gateway Failover](15%20-%20Lab%20-%20HSRP%20Gateway%20Failover.md) · [Next: 17 - RIPv2 →](17%20-%20RIPv2.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
