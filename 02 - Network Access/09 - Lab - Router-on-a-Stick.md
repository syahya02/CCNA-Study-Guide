# Lab - Router-on-a-Stick

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Allow three VLANs to communicate through one router interface with 802.1Q subinterfaces.

## Topology

```text
PC10 -- Fa0/2
PC20 -- Fa0/3 -- SW1 Fa0/1 === trunk === R1 G0/0
PC30 -- Fa0/4
```

## Addressing / prerequisites
VLAN 10: `10.10.10.10/8` gateway `10.10.10.1`; VLAN 20: `150.150.150.20/16` gateway `150.150.150.1`; VLAN 30: `192.168.1.30/24` gateway `192.168.1.1`.

## Configuration

### R1

```cisco
conf t
interface g0/0
 no ip address
 no shutdown
interface g0/0.10
 encapsulation dot1Q 10
 ip address 10.10.10.1 255.0.0.0
interface g0/0.20
 encapsulation dot1Q 20
 ip address 150.150.150.1 255.255.0.0
interface g0/0.30
 encapsulation dot1Q 30
 ip address 192.168.1.1 255.255.255.0
end
wr
```

### SW1

```cisco
conf t
vlan 10
 name HR
vlan 20
 name IT
vlan 30
 name FINANCE
interface fa0/1
 switchport mode trunk
interface fa0/2
 switchport mode access
 switchport access vlan 10
interface fa0/3
 switchport mode access
 switchport access vlan 20
interface fa0/4
 switchport mode access
 switchport access vlan 30
end
wr
```

## Verify

```cisco
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
```

## Troubleshooting and expected result
Use the listed PC masks **and default gateways**. PC10 should reach PC20 and PC30 once inter-VLAN routing is working, **without RIP** (all VLAN networks are directly connected to R1).

## Related notes
[Router-on-a-Stick and SVI Routing](08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md) · [VLANs](02%20-%20VLANs.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md)

---
[← Previous: 08 - Router-on-a-Stick and SVI Routing](08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md) · [Next: 10 - Lab - Multilayer SVI Routing →](10%20-%20Lab%20-%20Multilayer%20SVI%20Routing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
