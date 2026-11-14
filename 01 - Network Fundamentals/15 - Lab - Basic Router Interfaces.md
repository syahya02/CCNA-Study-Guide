# Lab - Basic Router Interfaces

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Assign two directly connected IPv4 networks to a router and confirm interface status.

## Topology

```text
SW1 --- R1 --- SW2
```

## Addressing / prerequisites
R1 G0/0/0 = `10.10.10.1/8`; R1 G0/0/1 = `150.0.0.1/16`. These are the addresses from the original 04/10 practical; use them only in an isolated lab.

## Configuration

### R1

```cisco
enable
configure terminal
hostname R1
interface g0/0/0
 ip address 10.10.10.1 255.0.0.0
 no shutdown
exit
interface g0/0/1
 ip address 150.0.0.1 255.255.0.0
 no shutdown
end
write memory
```

### SW1 and SW2

```cisco
enable
configure terminal
hostname SW1
end
write memory
! Repeat on the second switch using hostname SW2
```

## Verify

```cisco
show ip interface brief
show ip route connected
show running-config
```

## Troubleshooting and expected result
Both router interfaces should show up/up when connected to active devices. The route table automatically contains the two connected networks; no routing protocol is needed.

## Related notes
[IPv4 Addressing](11%20-%20IPv4%20Addressing.md) · [Network Foundations](01%20-%20Network%20Foundations.md) · [Cisco IOS Command Reference](../07%20-%20Cisco%20IOS%20Command%20Reference/01%20-%20Cisco%20IOS%20Command%20Reference.md)

---
[← Previous: 14 - Lab - IPv4 Subnetting Practice](14%20-%20Lab%20-%20IPv4%20Subnetting%20Practice.md) · [Next: 16 - IPv6 Addressing →](16%20-%20IPv6%20Addressing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
