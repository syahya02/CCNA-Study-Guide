# Lab - Static NAT and Dynamic NAT Pool

> **Core CCNA lab** · **Platform:** Packet Tracer · **Status:** Configuration guide, not simulator-verified.

## Objective
Compare a fixed 1:1 translation with an address borrowed from a public-address pool.

## Topology
`PC1, PC2 — SW1 — R1 (NAT) — R2 — Server`

| Device/interface | IP |
|---|---|
| R1 inside G0/0 | `192.168.10.1/24` |
| R1 outside G0/1 | `203.0.113.1/24` |
| R2 WAN G0/0 | `203.0.113.2/24` |
| R2 server G0/1 | `198.51.100.1/24` |
| PC1 | `192.168.10.10/24`, GW `.1` |
| PC2 | `192.168.10.11/24`, GW `.1` |
| Server | `198.51.100.10/24`, GW `198.51.100.1` |

## R1 configuration
```cisco
enable
configure terminal
hostname R1
interface gigabitEthernet0/0
 ip address 192.168.10.1 255.255.255.0
 ip nat inside
 no shutdown
exit
interface gigabitEthernet0/1
 ip address 203.0.113.1 255.255.255.0
 ip nat outside
 no shutdown
exit
ip route 198.51.100.0 255.255.255.0 203.0.113.2
ip nat inside source static 192.168.10.10 203.0.113.10
access-list 1 permit host 192.168.10.11
ip nat pool DEMO 203.0.113.20 203.0.113.30 netmask 255.255.255.0
ip nat inside source list 1 pool DEMO
end
write memory
```

## R2 configuration
```cisco
enable
configure terminal
hostname R2
interface gigabitEthernet0/0
 ip address 203.0.113.2 255.255.255.0
 no shutdown
exit
interface gigabitEthernet0/1
 ip address 198.51.100.1 255.255.255.0
 no shutdown
end
```

## Verify
From PC1 and PC2 separately ping `198.51.100.10`. On R1:
```cisco
show ip nat translations
show ip nat statistics
show access-lists
```

**Expected:** PC1's inside global is `203.0.113.10`; PC2 receives an address from the `203.0.113.20`–`.30` pool. Exact transient ICMP entries depend on traffic and simulator behaviour.

## Troubleshoot
Check NAT inside/outside markings, route to server, PC gateways, ACL matching PC2, and ARP/reachability of translated pool addresses.

## Lesson learned
Static NAT fixes one mapping; dynamic NAT consumes addresses from a finite pool; PAT shares an address among many connections.

---
[← Previous: 07 - Lab - NAT and PAT](07%20-%20Lab%20-%20NAT%20and%20PAT.md) · [Next: 09 - NTP and SNMP Syslog →](09%20-%20NTP%20and%20SNMP%20Syslog.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
