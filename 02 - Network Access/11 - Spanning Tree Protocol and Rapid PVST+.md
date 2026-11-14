# Spanning Tree Protocol and Rapid PVST+

## Why it exists
Redundant Layer 2 paths can cause frames to circulate endlessly, creating broadcast storms and MAC flapping. STP prevents loops **without removing backup cables**.

## Election and roles
1. The **lowest Bridge ID** (priority plus VLAN system ID and MAC) wins the root bridge election.
2. Each non-root switch picks a **root port** — its best path to the root.
3. Each network segment has a **designated port**. Other redundant ports may be **alternate/discarding**.
4. In Rapid PVST+, major states are **discarding, learning, forwarding**; backup paths can transition faster than legacy STP.

```cisco
spanning-tree mode rapid-pvst
spanning-tree vlan 10 root primary
show spanning-tree vlan 10
```

**Protection:** PortFast for host-facing ports; BPDU Guard disables an edge port receiving unexpected BPDUs; root guard prevents a neighbor from becoming root; loop guard protects against loss of BPDUs; BPDU filter must be used carefully because it can undermine loop prevention.

STP decisions are **per VLAN** with Rapid PVST+. Root selection isn't based on switch hostname.

## Practise this topic

- [Lab - STP Redundant Links](12%20-%20Lab%20-%20STP%20Redundant%20Links.md)

---
[← Previous: 10 - Lab - Multilayer SVI Routing](10%20-%20Lab%20-%20Multilayer%20SVI%20Routing.md) · [Next: 12 - Lab - STP Redundant Links →](12%20-%20Lab%20-%20STP%20Redundant%20Links.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
