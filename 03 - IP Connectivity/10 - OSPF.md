# OSPF

**Open Shortest Path First (OSPF)** is a link-state IGP that calculates paths using link-state information and a cost metric. For IPv4, OSPF is IP protocol **89** (not TCP/UDP port 89). Default AD is **110**.

## Key ideas
- Routers exchange **Hello** packets and form neighbors on matching links.
- Routers build a link-state database and run SPF for route selection.
- **Area 0** is the backbone used for normal inter-area communication.
- **ABR**: Area Border Router, participates in Area 0 and another area.
- `O` = intra-area route, `O IA` = inter-area route in `show ip route`.

## Cisco configuration
```cisco
router ospf 1
 network 10.0.0.0 0.0.0.255 area 0
```

**Critical:** OSPF `network` statements use **wildcard masks**, the inverse of subnet masks. `/24` mask `255.255.255.0` → wildcard `0.0.0.255`.

To avoid ambiguity, match the exact interface IP:
```cisco
router ospf 1
 network 1.1.1.1 0.0.0.0 area 0
```

Some Packet Tracer images have normalized input matching a subnet mask; use the documented wildcard form for consistent configurations.

## Multi-area lab nuance
In the sample multi-area lab, R1 has Loopback0 `50.50.50.1/8` in Area 0 and two physical links in Area 1 and Area 2. This can demonstrate one ABR with multiple areas in Packet Tracer, but a normal production design should use a connected **Area 0 transit backbone** for multi-router inter-area routing. A loopback alone is not a substitute for a network-wide backbone topology.

## Verify
```cisco
show ip ospf neighbor
show ip ospf interface brief
show ip ospf database
show ip route ospf
```

## Related
[Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md) · [Lab - Single-Area OSPF](12%20-%20Lab%20-%20Single-Area%20OSPF.md) · [Lab - Multi-Area OSPF](23%20-%20Lab%20-%20Multi-Area%20OSPF.md)

---
[← Previous: 09 - Static Route Variants](09%20-%20Static%20Route%20Variants.md) · [Next: 11 - OSPF Router ID and DR BDR →](11%20-%20OSPF%20Router%20ID%20and%20DR%20BDR.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
