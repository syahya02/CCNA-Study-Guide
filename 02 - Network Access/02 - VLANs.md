# VLANs

A **Virtual LAN (VLAN)** logically separates one physical switched network into multiple **Layer 2 broadcast domains**. Each VLAN commonly uses a distinct IP subnet.

Example: VLAN 10 = HR (`192.168.10.0/24`); VLAN 20 = IT (`192.168.20.0/24`). Devices in different VLANs need a Layer 3 gateway to communicate.

## Access ports and trunks

- **Access port**: carries one access VLAN, typically to a PC/router interface.
- **Trunk port**: carries multiple VLANs with 802.1Q tags, commonly between switches or a router-on-a-stick.

```cisco
conf t
vlan 10
 name HR
vlan 20
 name IT
interface fa0/1
 switchport mode access
 switchport access vlan 10
interface fa0/24
 switchport mode trunk
end
show vlan brief
show interfaces trunk
```

## Mistake from training
If R1 is attached to SW1 access VLAN 10, but R2 is attached to SW2 access VLAN 20, a trunk between the switches **does not translate VLAN 10 into VLAN 20**. They remain separate Layer 2 domains; use the same VLAN for a common direct subnet, or add Layer 3 routing.

## Why VLANs matter for firewall labs
They let you separate HR, IT, guests, servers and management and enforce policy between routed segments.

## Related
[Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md) · [Router-on-a-Stick and SVI Routing](08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md) · [VTP](20%20-%20VTP.md) · [Lab - Router-on-a-Stick](09%20-%20Lab%20-%20Router-on-a-Stick.md)

---
[← Previous: 01 - Switching and MAC Learning](01%20-%20Switching%20and%20MAC%20Learning.md) · [Next: 03 - Trunking and 802.1Q →](03%20-%20Trunking%20and%20802.1Q.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
