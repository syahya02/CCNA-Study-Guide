# Lab - Multi-Area OSPF

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Recreate the working three-router ABR demonstration from the training lab.

## Topology

```text
R2 --- Area 1 --- R1 --- Area 2 --- R3
                   Lo0 in Area 0
```

## Addressing / prerequisites
This addressing recreates a working `show running-config` example. R1 G0/0/0 `1.1.1.1/8`, G0/0/1 `2.2.2.1/8`, Lo0 `50.50.50.1/8`. R2 G0/0 `1.1.1.2/8`, Lo0 `70.70.70.1/8`, Lo1 `150.150.150.1/16`, Lo2 `192.168.1.1/24`. R3 G0/0 `2.2.2.2/8`, Lo0 `80.80.80.1/8`, Lo1 `160.160.160.1/16`, Lo2 `199.199.199.1/24`. Physical interfaces/loopbacks must be created before these OSPF commands.

## Physical interface and loopback setup

These assignments reproduce the interface details from the supplied working **show run** (no other physical interface settings are needed for the learning objective).

### R1
```cisco
conf t
interface g0/0/0
 ip address 1.1.1.1 255.0.0.0
 no shutdown
interface g0/0/1
 ip address 2.2.2.1 255.0.0.0
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
interface loopback 0
 ip address 70.70.70.1 255.0.0.0
interface loopback 1
 ip address 150.150.150.1 255.255.0.0
interface loopback 2
 ip address 192.168.1.1 255.255.255.0
end
```
### R3
```cisco
conf t
interface g0/0
 ip address 2.2.2.2 255.0.0.0
 no shutdown
interface loopback 0
 ip address 80.80.80.1 255.0.0.0
interface loopback 1
 ip address 160.160.160.1 255.255.0.0
interface loopback 2
 ip address 199.199.199.1 255.255.255.0
end
```

## Routing protocol configuration

### R1 — ABR

```cisco
conf t
router ospf 1
 network 50.50.50.1 0.0.0.0 area 0
 network 1.1.1.1 0.0.0.0 area 1
 network 2.2.2.1 0.0.0.0 area 2
end
wr
```

### R2

```cisco
conf t
router ospf 1
 network 1.1.1.2 0.0.0.0 area 1
 network 70.70.70.1 0.0.0.0 area 1
 network 150.150.150.1 0.0.0.0 area 1
 network 192.168.1.1 0.0.0.0 area 1
end
wr
```

### R3

```cisco
conf t
router ospf 1
 network 2.2.2.2 0.0.0.0 area 2
 network 80.80.80.1 0.0.0.0 area 2
 network 160.160.160.1 0.0.0.0 area 2
 network 199.199.199.1 0.0.0.0 area 2
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
R1 should form neighbors with R2 and R3. Verify remote routes (`O`/`O IA`) before claiming success. Test `R2# ping 80.80.80.1` and `R3# ping 70.70.70.1`.

## Notes and corrections
**Design warning:** Area 0 only on a loopback is a narrow single-ABR lab arrangement, **not** the recommended backbone topology for production. In a real multi-ABR network, use connected Area 0 transit connectivity. OSPF wildcard syntax is standard; some Packet Tracer images normalized subnet-mask-looking input.

## Related notes
[OSPF](10%20-%20OSPF.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---
[← Previous: 22 - OSPF Multi-Area](22%20-%20OSPF%20Multi-Area.md) · [Next: 24 - Serial WAN Basics →](24%20-%20Serial%20WAN%20Basics.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
