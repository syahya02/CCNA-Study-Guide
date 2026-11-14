# Lab - NAT and PAT

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Translate inside PC traffic to R1 WAN interface address before reaching a remote server.

## Topology

```text
PC1 -- R1 (NAT) -- R2 -- Server
```

## Addressing / prerequisites
PC1 `192.168.1.10/24` gw `192.168.1.1`; R1 G0/0 inside `192.168.1.1/24`, G0/1 outside `10.0.0.1/30`; R2 G0/0 `10.0.0.2/30`, G0/1 `203.0.113.1/24`; server `203.0.113.10/24` gw `203.0.113.1`. `203.0.113.0/24` is documentation-only.

## Configuration

### R1

```cisco
enable
conf t
hostname R1
interface g0/0
 ip address 192.168.1.1 255.255.255.0
 ip nat inside
 no shutdown
interface g0/1
 ip address 10.0.0.1 255.255.255.252
 ip nat outside
 no shutdown
exit
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
ip route 203.0.113.0 255.255.255.0 10.0.0.2
end
wr
```

### R2

```cisco
enable
conf t
hostname R2
interface g0/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown
interface g0/1
 ip address 203.0.113.1 255.255.255.0
 no shutdown
end
wr
```

## Verify

```cisco
show ip nat translations
show ip nat statistics
show ip interface brief
show access-lists
```

## Troubleshooting and expected result
From PC1 `ping 203.0.113.10`; after traffic, R1 should show NAT translations from `192.168.1.10` to `10.0.0.1` (ICMP identifier may be included). The R2-to-server side does not need to route to the original private source for PAT replies.

## Related notes
[NAT and PAT](05%20-%20NAT%20and%20PAT.md) · [ACLs](../05%20-%20Security%20Fundamentals/04%20-%20ACLs.md) · [Static and Default Routing](../03%20-%20IP%20Connectivity/04%20-%20Static%20and%20Default%20Routing.md)

---
[← Previous: 06 - NAT Types and Translation Pools](06%20-%20NAT%20Types%20and%20Translation%20Pools.md) · [Next: 08 - Lab - Static NAT and Dynamic NAT Pool →](08%20-%20Lab%20-%20Static%20NAT%20and%20Dynamic%20NAT%20Pool.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
