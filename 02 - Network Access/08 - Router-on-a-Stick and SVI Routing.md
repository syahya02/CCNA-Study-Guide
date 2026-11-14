# Router-on-a-Stick and SVI Routing

Both methods route traffic **between VLANs**. They are different from dynamic routing protocols such as RIP and OSPF.

## Router-on-a-stick (single physical router link)

A switch-to-router **trunk** carries several VLANs. Router subinterfaces each get an 802.1Q tag and IP gateway.

```cisco
interface g0/0
 no ip address
 no shutdown
interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
interface g0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

## Layer 3 switching (SVIs)

A switch virtual interface (`interface vlan 10`) is the gateway for VLAN 10. On a multilayer switch, enable `ip routing`.

```cisco
ip routing
interface vlan 10
 ip address 192.168.10.1 255.255.255.0
 no shutdown
interface vlan 20
 ip address 192.168.20.1 255.255.255.0
 no shutdown
```

> SVIs depend on VLAN operational state (usually an active member/trunk port). An IP address on a routed physical port requires `no switchport` on supported multilayer switches.

## Related
[VLANs](02%20-%20VLANs.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md) · [Lab - Router-on-a-Stick](09%20-%20Lab%20-%20Router-on-a-Stick.md) · [Lab - Multilayer SVI Routing](10%20-%20Lab%20-%20Multilayer%20SVI%20Routing.md)

---

## Practise this topic

- [Lab - Router-on-a-Stick](09%20-%20Lab%20-%20Router-on-a-Stick.md)
- [Lab - Multilayer SVI Routing](10%20-%20Lab%20-%20Multilayer%20SVI%20Routing.md)

---
[← Previous: 07 - Lab - CDP and LLDP Discovery](07%20-%20Lab%20-%20CDP%20and%20LLDP%20Discovery.md) · [Next: 09 - Lab - Router-on-a-Stick →](09%20-%20Lab%20-%20Router-on-a-Stick.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
