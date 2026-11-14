# Lab - RIPv2 and Loopbacks

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Advertise multiple loopback networks dynamically across three routers.

## Topology

```text
R1 1.1.1.1/8 --- 1.1.1.2/8 R2 2.2.2.1/8 --- 2.2.2.2/8 R3
```

## Addressing / prerequisites
R1 loopbacks: `10.1.1.1/8`, `150.150.1.1/16`, `200.200.200.1/24`; R2: `20.1.1.1/8`, `160.160.1.1/16`, `210.210.210.1/24`; R3: `30.1.1.1/8`, `170.170.1.1/16`, `220.220.220.1/24`. Assume physical interfaces already configured/up as shown.

## Configuration

### R1

```cisco
conf t
interface lo0
 ip address 10.1.1.1 255.0.0.0
interface lo1
 ip address 150.150.1.1 255.255.0.0
interface lo2
 ip address 200.200.200.1 255.255.255.0
router rip
 version 2
 no auto-summary
 network 1.0.0.0
 network 10.0.0.0
 network 150.150.0.0
 network 200.200.200.0
end
wr
```

### R2

```cisco
conf t
interface lo0
 ip address 20.1.1.1 255.0.0.0
interface lo1
 ip address 160.160.1.1 255.255.0.0
interface lo2
 ip address 210.210.210.1 255.255.255.0
router rip
 version 2
 no auto-summary
 network 1.0.0.0
 network 2.0.0.0
 network 20.0.0.0
 network 160.160.0.0
 network 210.210.210.0
end
wr
```

### R3

```cisco
conf t
interface lo0
 ip address 30.1.1.1 255.0.0.0
interface lo1
 ip address 170.170.1.1 255.255.0.0
interface lo2
 ip address 220.220.220.1 255.255.255.0
router rip
 version 2
 no auto-summary
 network 2.0.0.0
 network 30.0.0.0
 network 170.170.0.0
 network 220.220.220.0
end
wr
```

## Verify

```cisco
show ip protocols
show ip route rip
show ip interface brief
ping 30.1.1.1
```

## Troubleshooting and expected result
R1 learns R2 loopbacks at 1 RIP hop and R3 loopbacks at 2 RIP hops. `no auto-summary` is recommended even though examples use old classful masks.

## Related notes
[RIPv2](17%20-%20RIPv2.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---
[← Previous: 17 - RIPv2](17%20-%20RIPv2.md) · [Next: 19 - Lab - RIP Across VLAN Switch Links →](19%20-%20Lab%20-%20RIP%20Across%20VLAN%20Switch%20Links.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
