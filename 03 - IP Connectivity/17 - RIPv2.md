# RIPv2

> **Supplementary:** useful networking knowledge beyond the main CCNA v1.1 configuration objectives.

**Routing Information Protocol version 2 (RIPv2)** is a distance-vector protocol that advertises routes using **hop count**. Maximum usable hop count is **15**; 16 means unreachable. Default administrative distance is **120**. It uses UDP **520** for IPv4.

## Example topology and configuration
```text
R1 ----- R2 ----- R3
1.0.0.0/8   2.0.0.0/8
```

```cisco
router rip
 version 2
 no auto-summary
 network 1.0.0.0
 network 10.0.0.0
```

- `router rip`: enable RIP process.
- `version 2`: exchange RIPv2 updates.
- `network`: selects interfaces in a **classful major network** to run RIP and advertise their connected prefixes.
- `no auto-summary`: prevents automatic classful summarization at network boundaries. It is usually good practice, but may not alter a classful `/8`, `/16`, `/24` example.

## Example
With R3 Loopback0 `30.1.1.1/8`, R1 can learn `30.0.0.0/8` via R2. Routing table marker: `R`.

## Verify
```cisco
show ip protocols
show ip route rip
show ip interface brief
```

## Related
[Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Lab - RIPv2 and Loopbacks](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md)

---

## Practise this topic

- [Lab - RIPv2 and Loopbacks](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md)
- [Lab - RIP Across VLAN Switch Links](19%20-%20Lab%20-%20RIP%20Across%20VLAN%20Switch%20Links.md)

---
[← Previous: 16 - Routing Troubleshooting](16%20-%20Routing%20Troubleshooting.md) · [Next: 18 - Lab - RIPv2 and Loopbacks →](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
