# Switching Commands

```cisco
vlan 10
 name HR
interface fa0/1
 switchport mode access
 switchport access vlan 10
interface g0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```

| Command | Use |
|---|---|
| `show vlan brief` | VLAN list/access ports |
| `show interfaces trunk` | Trunk state and allowed VLANs |
| `show interfaces switchport` | Switchport mode/VLAN parameters |
| `show mac address-table` | Learned MACs/ports |
| `show spanning-tree` | STP topology |
| `show etherchannel summary` | LACP/port-channel health |
| `show vtp status` | VTP mode/domain/revision |
| `ip routing` | Enable routing on supported multilayer switch |
| `interface vlan 10` | Configure SVI |
| `no switchport` | Convert suitable L3 switchport into routed port |

## Related
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [Router-on-a-Stick and SVI Routing](../02%20-%20Network%20Access/08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md) · [STP and EtherChannel](../02%20-%20Network%20Access/11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md)

---

[← Main study guide](../README.md)

---
[← Previous: 02 - Interface and IPv4 Commands](02%20-%20Interface%20and%20IPv4%20Commands.md) · [Next: 04 - Routing Commands →](04%20-%20Routing%20Commands.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
