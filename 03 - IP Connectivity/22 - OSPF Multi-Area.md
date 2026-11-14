# OSPF Multi-Area

> **Supplementary:** detailed multi-area OSPF configuration goes beyond the core CCNA v1.1 single-area OSPF objective.

OSPF uses **Area 0 as the backbone**. An Area Border Router (ABR) participates in Area 0 and at least one other area. Inter-area routes may appear as `O IA`.

```cisco
router ospf 1
 network 10.0.12.0 0.0.0.255 area 0
 network 10.0.13.0 0.0.0.255 area 1
```

**Lab nuance:** in the training exercise, R1's loopback belongs to Area 0 while two physical links are in areas 1 and 2. That is a specific single-ABR demonstration, **not a blueprint for a routed Area 0 transit backbone** in a multi-ABR production network. Real designs normally establish Area 0 connectivity on transit links.

See the multi-area lab for the actual training topology and the verification steps.

## Practise this topic

- [Lab - Multi-Area OSPF](23%20-%20Lab%20-%20Multi-Area%20OSPF.md)

---
[← Previous: 21 - Lab - EIGRP Routing](21%20-%20Lab%20-%20EIGRP%20Routing.md) · [Next: 23 - Lab - Multi-Area OSPF →](23%20-%20Lab%20-%20Multi-Area%20OSPF.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
