# Lab - EIGRP Routing

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Use EIGRP to advertise routed links and loopback networks.

## Topology

```text
R1 --(1.0.0.0/8)-- R2 --(2.0.0.0/8)-- R3 --(3.0.0.0/8)-- R4
```

## Addressing / prerequisites
Based on four-router 12/10 training network. Physical links: R1 `1.1.1.1`, R2 `1.1.1.2` and `2.2.2.1`, R3 `2.2.2.2` and `3.3.3.1`, R4 `3.3.3.3`, all /8. Example Loopback0 R1 `50.50.50.1/8`, R2 `60.60.60.1/8`, R3 `70.70.70.1/8`, R4 `80.80.80.1/8`. Configure physical interfaces and loopbacks first (see source), then:

## Physical interface and loopback setup

The source exercise used **four routers**. Configure the connected interfaces and one representative loopback per router before entering EIGRP commands.

### R1: connected link and Lo0
```cisco
conf t
interface g0/0
 ip address 1.1.1.1 255.0.0.0
 no shutdown
interface loopback 0
 ip address 50.50.50.1 255.0.0.0
end
```
### R2: both links and Lo0
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
### R3: both links and Lo0
```cisco
conf t
interface g0/0
 ip address 2.2.2.2 255.0.0.0
 no shutdown
interface g0/1
 ip address 3.3.3.1 255.0.0.0
 no shutdown
interface loopback 0
 ip address 70.70.70.1 255.0.0.0
end
```
### R4: link and Lo0
```cisco
conf t
interface g0/0
 ip address 3.3.3.3 255.0.0.0
 no shutdown
interface loopback 0
 ip address 80.80.80.1 255.0.0.0
end
```

> A larger variant of this lab adds multiple loopback networks. This simplified supplementary exercise uses one per router to focus on EIGRP fundamentals.

## Routing protocol configuration

### R1

```cisco
conf t
router eigrp 100
 no auto-summary
 network 1.0.0.0
 network 50.0.0.0
end
wr
```

### R2

```cisco
conf t
router eigrp 100
 no auto-summary
 network 1.0.0.0
 network 2.0.0.0
 network 60.0.0.0
end
wr
```

### R3

```cisco
conf t
router eigrp 100
 no auto-summary
 network 2.0.0.0
 network 3.0.0.0
 network 70.0.0.0
end
wr
```

### R4

```cisco
conf t
router eigrp 100
 no auto-summary
 network 3.0.0.0
 network 80.0.0.0
end
wr
```

## Verify

```cisco
show ip eigrp neighbors
show ip eigrp topology
show ip route eigrp
```

## Troubleshooting and expected result
EIGRP neighbors should form over the link networks and remote loopbacks should appear as `D`. Match AS number on adjacent routers and ensure interfaces are up.

## Notes and corrections
This is a simplified **routing stage** from the larger source configuration; remaining loopbacks can be added with corresponding major-network statements. EIGRP is supplementary to CCNA 200-301 v1.1.

## Related notes
[EIGRP](20%20-%20EIGRP.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md) · [Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---
[← Previous: 20 - EIGRP](20%20-%20EIGRP.md) · [Next: 22 - OSPF Multi-Area →](22%20-%20OSPF%20Multi-Area.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
