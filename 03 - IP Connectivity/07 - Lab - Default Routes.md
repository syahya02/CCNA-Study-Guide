# Lab - Default Routes

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Show how a catch-all `0.0.0.0/0` route works between two routers.

## Topology

```text
R1 1.1.1.1/8 ------ 1.1.1.2/8 R2
Lo0 10.10.10.1/8             Lo0 192.168.1.1/24
```

## Addressing / prerequisites
Adapt `g0/0` to the router model. On broadcast links, a next-hop IP is generally clearer than a static route naming only the outgoing Ethernet interface.

## Configuration

### R1

```cisco
conf t
interface g0/0
 ip address 1.1.1.1 255.0.0.0
 no shut
interface loopback 0
 ip address 10.10.10.1 255.0.0.0
exit
ip route 0.0.0.0 0.0.0.0 1.1.1.2
end
wr
```

### R2

```cisco
conf t
interface g0/0
 ip address 1.1.1.2 255.0.0.0
 no shut
interface loopback 0
 ip address 192.168.1.1 255.255.255.0
exit
ip route 0.0.0.0 0.0.0.0 1.1.1.1
end
wr
```

## Verify

```cisco
show ip route
ping 192.168.1.1
ping 10.10.10.1
```

## Troubleshooting and expected result
Each router uses the default route if no more-specific route exists. In a real enterprise, avoid relying on opposing defaults without understanding the resulting paths and possible loops.

## Related notes
[Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---
[← Previous: 06 - Lab - Static Routing Across VLAN Links](06%20-%20Lab%20-%20Static%20Routing%20Across%20VLAN%20Links.md) · [Next: 08 - Lab - IPv6 Static Routes →](08%20-%20Lab%20-%20IPv6%20Static%20Routes.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
