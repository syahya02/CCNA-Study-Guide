# Native and Voice VLANs

- **Access VLAN:** untagged data traffic for a typical endpoint.
- **Voice VLAN:** allows an IP phone and PC to share one switch port while separating voice traffic logically; the phone typically tags its voice frames.
- **Native VLAN:** on an 802.1Q trunk, frames belonging to the native VLAN are untagged by default; native VLANs should match on both ends.
- **Default VLAN:** VLAN 1 exists on many Cisco switches; a best practice is to use dedicated VLANs for users and management where feasible.

```cisco
interface fastEthernet 0/10
 switchport mode access
 switchport access vlan 10
 switchport voice vlan 20

interface gigabitEthernet 0/1
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,99
```

**Verify:** `show interfaces trunk`, `show interfaces fa0/10 switchport`. A voice VLAN does not automatically provide voice QoS; additional policy may be needed.

---
[← Previous: 04 - Lab - VLANs and Trunks](04%20-%20Lab%20-%20VLANs%20and%20Trunks.md) · [Next: 06 - CDP and LLDP →](06%20-%20CDP%20and%20LLDP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
