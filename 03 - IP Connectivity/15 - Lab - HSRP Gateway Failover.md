# Lab - HSRP Gateway Failover

> **Core CCNA concept with supplementary hands-on practice** · **Platform:** Packet Tracer; check HSRP support on selected routers.

## Objective
Provide one stable default gateway across two physical routers.

## Topology / addresses
`PC1 — SW1 — R1 G0/0` and `SW1 — R2 G0/0`

| Device | Address |
|---|---|
| Virtual gateway (HSRP group 1) | `192.168.10.1/24` |
| R1 LAN | `192.168.10.2/24` |
| R2 LAN | `192.168.10.3/24` |
| PC1 | `192.168.10.10/24`, gateway `192.168.10.1` |

## R1
```cisco
conf t
interface gigabitEthernet0/0
 ip address 192.168.10.2 255.255.255.0
 standby 1 ip 192.168.10.1
 standby 1 priority 110
 standby 1 preempt
 no shutdown
end
```
## R2
```cisco
conf t
interface gigabitEthernet0/0
 ip address 192.168.10.3 255.255.255.0
 standby 1 ip 192.168.10.1
 standby 1 priority 100
 standby 1 preempt
 no shutdown
end
```

## Verify and failover
```cisco
show standby brief
show ip interface brief
```
From PC1 ping `192.168.10.1`; shut R1's LAN interface and confirm R2 becomes active. Restore the interface and verify re-election.

## Troubleshooting
Check matching group, virtual IP, VLAN, HSRP compatibility, and device support. This lab tests **gateway availability only**, not a complete upstream Internet failover path.

## Lesson learned
A virtual default gateway stays consistent as the active router changes.

---
[← Previous: 14 - First Hop Redundancy Protocols](14%20-%20First%20Hop%20Redundancy%20Protocols.md) · [Next: 16 - Routing Troubleshooting →](16%20-%20Routing%20Troubleshooting.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
