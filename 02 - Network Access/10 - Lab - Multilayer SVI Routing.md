# Lab - Multilayer SVI Routing

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Route between four VLANs on two Layer 3 switches using SVIs, routed uplink and static routes.

## Topology

```text
PC10 -- MLS1 -- 10.0.0.0/30 -- MLS2 -- PC30
PC20 --|                             |-- PC40
```

## Addressing / prerequisites
MLS1 VLAN 10 `192.168.10.1/24`, VLAN 20 `192.168.20.1/24`; MLS2 VLAN 30 `192.168.30.1/24`, VLAN 40 `192.168.40.1/24`. Routed G0/1 uplink: MLS1 `10.0.0.1/30`, MLS2 `10.0.0.2/30`. Client addresses: `.10` in each corresponding subnet and gateway = SVI `.1`.

## Configuration

### MLS1

```cisco
enable
conf t
hostname MLS1
vlan 10
 name USERS
vlan 20
 name SERVERS
ip routing
interface vlan 10
 ip address 192.168.10.1 255.255.255.0
 no shutdown
interface vlan 20
 ip address 192.168.20.1 255.255.255.0
 no shutdown
interface fa0/1
 switchport mode access
 switchport access vlan 10
interface fa0/2
 switchport mode access
 switchport access vlan 20
interface g0/1
 no switchport
 ip address 10.0.0.1 255.255.255.252
 no shutdown
exit
ip route 192.168.30.0 255.255.255.0 10.0.0.2
ip route 192.168.40.0 255.255.255.0 10.0.0.2
end
wr
```

### MLS2

```cisco
enable
conf t
hostname MLS2
vlan 30
 name USERS_REMOTE
vlan 40
 name SERVERS_REMOTE
ip routing
interface vlan 30
 ip address 192.168.30.1 255.255.255.0
 no shutdown
interface vlan 40
 ip address 192.168.40.1 255.255.255.0
 no shutdown
interface fa0/1
 switchport mode access
 switchport access vlan 30
interface fa0/2
 switchport mode access
 switchport access vlan 40
interface g0/1
 no switchport
 ip address 10.0.0.2 255.255.255.252
 no shutdown
exit
ip route 192.168.10.0 255.255.255.0 10.0.0.1
ip route 192.168.20.0 255.255.255.0 10.0.0.1
end
wr
```

## Verify

```cisco
show vlan brief
show ip interface brief
show ip route
show running-config
```

## Troubleshooting and expected result
SVI `up/up` needs operational VLAN presence; check active access ports/VLAN state. Verify PC1 (`192.168.10.10`) can ping PC3 (`192.168.30.10`).

## Related notes
[Router-on-a-Stick and SVI Routing](08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md) · [VLANs](02%20-%20VLANs.md) · [Static and Default Routing](../03%20-%20IP%20Connectivity/04%20-%20Static%20and%20Default%20Routing.md)

---
[← Previous: 09 - Lab - Router-on-a-Stick](09%20-%20Lab%20-%20Router-on-a-Stick.md) · [Next: 11 - Spanning Tree Protocol and Rapid PVST+ →](11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
