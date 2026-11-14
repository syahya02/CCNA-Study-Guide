# Trunking and 802.1Q

**IEEE 802.1Q** adds a VLAN identifier to Ethernet frames on a trunk. A trunk carries traffic for several VLANs across one physical link.

## Configuration
```cisco
interface gigabitEthernet0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
! Optional; requires consistent design on both ends:
 switchport trunk native vlan 99
```

- **Native VLAN**: normally untagged on an 802.1Q trunk by default; configure consistently at both ends.
- **Allowed VLAN list**: controls which tagged VLANs a trunk transports.
- The VLAN must exist/operate on the relevant switches for normal switching.

## Verify
```cisco
show interfaces trunk
show interfaces switchport
show vlan brief
```

## Related
[VLANs](02%20-%20VLANs.md) · [Router-on-a-Stick and SVI Routing](08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md)

---

## Practise this topic

- [Lab - VLANs and Trunks](04%20-%20Lab%20-%20VLANs%20and%20Trunks.md)

---
[← Previous: 02 - VLANs](02%20-%20VLANs.md) · [Next: 04 - Lab - VLANs and Trunks →](04%20-%20Lab%20-%20VLANs%20and%20Trunks.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
