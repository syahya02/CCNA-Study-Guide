# Lab - Static Routes and Loopbacks

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Learn to reach a remote loopback by manually adding a route in each direction.

## Topology

```text
R1 (1.1.1.1/8) -------- R2 (1.1.1.2/8)
 Lo0: 172.16.1.1/16       Lo0: 192.168.1.1/24
```

## Addressing / prerequisites
Link `1.0.0.0/8`. R1 loopback belongs to `172.16.0.0/16`, **not** `172.16.1.0/16`.

## Configuration

### R1

```cisco
conf t
hostname R1
interface g0/0
 ip address 1.1.1.1 255.0.0.0
 no shutdown
interface loopback 0
 ip address 172.16.1.1 255.255.0.0
exit
ip route 192.168.1.0 255.255.255.0 1.1.1.2
end
wr
```

### R2

```cisco
conf t
hostname R2
interface g0/0
 ip address 1.1.1.2 255.0.0.0
 no shutdown
interface loopback 0
 ip address 192.168.1.1 255.255.255.0
exit
ip route 172.16.0.0 255.255.0.0 1.1.1.1
end
wr
```

## Verify

```cisco
show ip route
show ip interface brief
ping 192.168.1.1
ping 172.16.1.1
```

## Troubleshooting and expected result
`S` routes appear for remote subnets. Check reverse routes if return pings fail.

## Notes and corrections
**Corrected from source:** `ip route 172.16.1.0 255.255.0.0 1.1.1.1` generates `%Inconsistent address and mask`; use `172.16.0.0/16`.

## Related notes
[Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md) · [Subnetting CIDR and VLSM](../01%20-%20Network%20Fundamentals/13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [Loopback Interfaces](01%20-%20Loopback%20Interfaces.md)

---
[← Previous: 04 - Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md) · [Next: 06 - Lab - Static Routing Across VLAN Links →](06%20-%20Lab%20-%20Static%20Routing%20Across%20VLAN%20Links.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
