# Lab - RIP Across VLAN Switch Links

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Use VLAN 10 and VLAN 20 only as Layer-2 paths for a three-router RIP topology.

## Topology

```text
R1 -- SW1(V10)==SW2(V10) -- R2 -- SW3(V20)==SW4(V20) -- R3
```

## Addressing / prerequisites
R1↔R2 = `1.0.0.0/8`; R2↔R3 = `2.0.0.0/8`. Switches separate the two segments but **do not perform inter-VLAN routing**. Use router configs and loopbacks from [Lab - RIPv2 and Loopbacks](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md).

## Configuration

### SW1 (R1-side)
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
wr
```

### SW2 (R2-side)
```cisco
conf t
vlan 10
 name HR
interface fa0/1
 switchport mode trunk
interface fa0/2
 switchport mode access
 switchport access vlan 10
end
wr
```

### SW3 (R2-side)
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
wr
```

### SW4 (R3-side)
```cisco
conf t
vlan 20
 name IT
interface fa0/1
 switchport mode trunk
interface fa0/2
 switchport mode access
 switchport access vlan 20
end
wr
```

### R1/R2/R3

```cisco
! Follow Lab 18 for complete RIP and loopback configuration.
! Switching does not change the Layer 3 RIP network numbers.
```

## Verify

```cisco
show interfaces trunk
show vlan brief
show ip protocols
show ip route rip
```

## Troubleshooting and expected result
Do **not** change just SW2's router-facing port to VLAN 20: traffic in VLAN 10 would no longer reach R2. RIP will not fix a missing Layer 2 path.

## Notes and corrections
This note references the full RIPv2 configuration in Lab 18 instead of duplicating dozens of lines unnecessarily.

## Related notes
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [RIPv2](17%20-%20RIPv2.md) · [Lab - RIPv2 and Loopbacks](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md)

---
[← Previous: 18 - Lab - RIPv2 and Loopbacks](18%20-%20Lab%20-%20RIPv2%20and%20Loopbacks.md) · [Next: 20 - EIGRP →](20%20-%20EIGRP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
