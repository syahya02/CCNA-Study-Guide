# Loopback Interfaces

A **loopback** is a virtual routed interface. It generally stays up while the router runs, regardless of external cabling.

## Example
```cisco
conf t
interface loopback 0
 ip address 10.1.1.1 255.0.0.0
end
show ip interface brief
```

## Why use loopbacks
Each router gained extra directly connected networks without additional PCs or physical cables. Static routes, RIP, EIGRP and OSPF could then demonstrate reachability to **remote loopback networks**.

**Example:** R3 owns `30.0.0.0/8`, which is **C** on R3 but **R** or **O** on R1 if learned through RIP or OSPF.

## Related
[RIPv2](17%20-%20RIPv2.md) · [OSPF](10%20-%20OSPF.md) · [EIGRP](20%20-%20EIGRP.md) · [Lab - RIPv2 and Loopbacks](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md)

---
[← Chapter study path](README.md) · [Next: 02 - Routing Table and Administrative Distance →](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
