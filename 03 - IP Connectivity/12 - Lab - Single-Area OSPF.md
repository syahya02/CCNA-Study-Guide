# Lab - Single-Area OSPF

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Advertise three routers’ networks in one OSPF backbone area.

## Topology

```text
R1 -- 1.0.0.0/8 -- R2 -- 2.0.0.0/8 -- R3
```

## Addressing / prerequisites
All interfaces area **0**. Link IPs: R1 `1.1.1.1/8`, R2 `1.1.1.2/8`, R2 `2.2.2.1/8`, R3 `2.2.2.2/8`. Each router optionally owns Loopback0 `50.50.50.1/8`, `60.60.60.1/8`, `70.70.70.1/8`.

## Physical interface and loopback setup

This example uses a three-router training topology. Enter the following first.

### R1
```cisco
conf t
interface g0/0
 ip address 1.1.1.1 255.0.0.0
 no shutdown
interface loopback 0
 ip address 50.50.50.1 255.0.0.0
end
```
### R2
```cisco
conf t
interface g0/0
 ip address 1.1.1.2 255.0.0.0
 no shutdown
interface g0/1
 ip address 2.2.2.1 255.0.0.0
 no shutdown
interface loopback 0
 ip address 60.60.60.1 255.0.0.0
end
```
### R3
```cisco
conf t
interface g0/0
 ip address 2.2.2.2 255.0.0.0
 no shutdown
interface loopback 0
 ip address 70.70.70.1 255.0.0.0
end
```

## Routing protocol configuration

### R1

```cisco
conf t
router ospf 1
 network 1.1.1.1 0.0.0.0 area 0
 network 50.50.50.1 0.0.0.0 area 0
end
wr
```

### R2

```cisco
conf t
router ospf 1
 network 1.1.1.2 0.0.0.0 area 0
 network 2.2.2.1 0.0.0.0 area 0
 network 60.60.60.1 0.0.0.0 area 0
end
wr
```

### R3

```cisco
conf t
router ospf 1
 network 2.2.2.2 0.0.0.0 area 0
 network 70.70.70.1 0.0.0.0 area 0
end
wr
```

## Verify

```cisco
show ip ospf neighbor
show ip ospf interface brief
show ip route ospf
show ip ospf database
```

## Troubleshooting and expected result
Neighbors form over matching OSPF-enabled physical interfaces. Loopback interfaces normally appear as /32 OSPF host routes unless configured differently for OSPF network type. Use exact-IP wildcard `0.0.0.0` to avoid ambiguity.

## Notes and corrections
The original exercise used four routers and showed subnet masks in some `network` lines. This compact three-router example demonstrates the same Area 0 mechanics; this guide focuses on the working steps.

## Related notes
[OSPF](10%20-%20OSPF.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---
[← Previous: 11 - OSPF Router ID and DR BDR](11%20-%20OSPF%20Router%20ID%20and%20DR%20BDR.md) · [Next: 13 - Lab - OSPF DR BDR Election →](13%20-%20Lab%20-%20OSPF%20DR%20BDR%20Election.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
