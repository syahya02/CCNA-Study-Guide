# Lab - VLANs and Trunks

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Create two VLANs across two switches and verify a shared VLAN reaches both sides.

## Topology

```text
PC10 -- SW1 === trunk === SW2 -- PC10
```

## Addressing / prerequisites
VLAN 10 = HR, VLAN 20 = IT. Both PC10 ports use access VLAN 10; trunks carry both VLANs.

## Configuration

### SW1

```cisco
conf t
vlan 10
 name HR
vlan 20
 name IT
interface fa0/1
 switchport mode access
 switchport access vlan 10
interface fa0/2
 switchport mode trunk
end
wr
```

### SW2

```cisco
conf t
vlan 10
 name HR
vlan 20
 name IT
interface fa0/1
 switchport mode trunk
interface fa0/2
 switchport mode access
 switchport access vlan 10
end
wr
```

## Verify

```cisco
show vlan brief
show interfaces trunk
show mac address-table
```

## Troubleshooting and expected result
Place both PCs in the same IP subnet for local pings. Changing one PC-facing port to VLAN 20 isolates it at Layer 2 even when the interswitch trunk carries both VLANs.

## Related notes
[VLANs](02%20-%20VLANs.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md) · [Switching and MAC Learning](01%20-%20Switching%20and%20MAC%20Learning.md)

---
[← Previous: 03 - Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md) · [Next: 05 - Native and Voice VLANs →](05%20-%20Native%20and%20Voice%20VLANs.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
