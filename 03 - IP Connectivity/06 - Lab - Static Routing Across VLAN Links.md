# Lab - Static Routing Across VLAN Links

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Practise route reachability across three routers connected through Layer 2 switch segments.

## Topology

```text
R1 -- SW1 == trunk == SW2 -- R2 -- SW3 == trunk == SW4 -- R3
```

## Addressing / prerequisites
Segment 1: `1.0.0.0/8`, VLAN 10; segment 2: `2.0.0.0/8`, VLAN 20. R1/R2 addresses `.1/.2`, R2/R3 addresses `.1/.2`. Add Loopback0 `10.10.10.1/8` on R1, `30.30.30.1/8` on R3 to test remote reachability.

## Configuration

### R1

```cisco
conf t
interface g0/0
 ip address 1.1.1.1 255.0.0.0
 no shut
interface lo0
 ip address 10.10.10.1 255.0.0.0
exit
ip route 2.0.0.0 255.0.0.0 1.1.1.2
ip route 30.0.0.0 255.0.0.0 1.1.1.2
end
wr
```

### R2

```cisco
conf t
interface g0/0
 ip address 1.1.1.2 255.0.0.0
 no shut
interface g0/1
 ip address 2.2.2.1 255.0.0.0
 no shut
exit
ip route 10.0.0.0 255.0.0.0 1.1.1.1
ip route 30.0.0.0 255.0.0.0 2.2.2.2
end
wr
```

### R3

```cisco
conf t
interface g0/0
 ip address 2.2.2.2 255.0.0.0
 no shut
interface lo0
 ip address 30.30.30.1 255.0.0.0
exit
ip route 1.0.0.0 255.0.0.0 2.2.2.1
ip route 10.0.0.0 255.0.0.0 2.2.2.1
end
wr
```

### SW1/SW2 (left segment)

```cisco
conf t
vlan 10
 name HR
interface fa0/1
 switchport mode access
 switchport access vlan 10
interface fa0/2
 switchport mode trunk
end
! SW2: its router port is also access VLAN 10;
! SW2 uplink to SW1 is trunk
```

### SW3/SW4 (right segment)

```cisco
conf t
vlan 20
 name IT
interface fa0/1
 switchport mode access
 switchport access vlan 20
interface fa0/2
 switchport mode trunk
end
! SW4 router-facing port must be access VLAN 20
```

## Verify

```cisco
show vlan brief
show interfaces trunk
show ip route
ping 30.30.30.1
```

## Troubleshooting and expected result
All router-facing switch ports on the same routed segment must remain in the same VLAN. Ping from R1 to R3 Loopback0 only after both-way routes exist.

## Notes and corrections
Switch interface numbers depend on the physical cabling; adapt access and trunk assignments instead of copying interface numbers without checking. This is an integrated example assembled from the training pattern.

## Related notes
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md)

---
[← Previous: 05 - Lab - Static Routes and Loopbacks](05%20-%20Lab%20-%20Static%20Routes%20and%20Loopbacks.md) · [Next: 07 - Lab - Default Routes →](07%20-%20Lab%20-%20Default%20Routes.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
