# OSPF Router ID and DR BDR

In **single-area OSPFv2**, neighbors exchange Hello packets, form adjacencies and learn routes from link-state advertisements.

## Router ID
A 32-bit dotted-decimal identifier, not necessarily an interface's reachable address. Selection typically uses: explicit `router-id`; otherwise highest loopback IP; otherwise highest active interface IP at process start. To change an already selected ID, the OSPF process may need to restart.

```cisco
router ospf 1
 router-id 1.1.1.1
```

## DR and BDR
On broadcast multiaccess Ethernet, OSPF elects a **Designated Router (DR)** and **Backup DR (BDR)** to reduce adjacency overhead. Higher OSPF priority wins; equal priority uses higher router ID. Priority 0 means **not eligible**. Elections are **non-preemptive**.

On point-to-point links, there is no DR/BDR election.

```cisco
show ip ospf interface
show ip ospf neighbor
```

Neighbor state `FULL` shows successful adjacency. `2WAY` between two DROTHER neighbors on broadcast networks can be normal.

## Practise this topic

- [Lab - Single-Area OSPF](12%20-%20Lab%20-%20Single-Area%20OSPF.md)
- [Lab - OSPF DR BDR Election](13%20-%20Lab%20-%20OSPF%20DR%20BDR%20Election.md)

---
[← Previous: 10 - OSPF](10%20-%20OSPF.md) · [Next: 12 - Lab - Single-Area OSPF →](12%20-%20Lab%20-%20Single-Area%20OSPF.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
