# First Hop Redundancy Protocols

A first-hop redundancy protocol provides a **virtual default-gateway address** so hosts do not depend on one physical router.

- **HSRP:** Cisco protocol, active/standby routers share a virtual IP/MAC.
- **VRRP:** standards-based equivalent with a master and backups.
- **GLBP:** Cisco mechanism that can distribute host gateway load across members (supplementary context).

End devices use the **virtual IP as their default gateway**, not the individual router address.

**Failure concept:** if the active gateway goes down, a standby member assumes the virtual gateway. The upstream routing design must also provide working paths, or gateway redundancy alone is not enough.

```cisco
interface g0/0
 standby 1 ip 192.168.10.1
 standby 1 priority 110
 standby 1 preempt
show standby brief
```

`preempt` allows a higher-priority router to regain active status after recovery; HSRP command support varies by platform.

## Practise this topic

- [Lab - HSRP Gateway Failover](15%20-%20Lab%20-%20HSRP%20Gateway%20Failover.md)

---
[← Previous: 13 - Lab - OSPF DR BDR Election](13%20-%20Lab%20-%20OSPF%20DR%20BDR%20Election.md) · [Next: 15 - Lab - HSRP Gateway Failover →](15%20-%20Lab%20-%20HSRP%20Gateway%20Failover.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
