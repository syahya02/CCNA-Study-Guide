# Lab - DHCP Snooping and DAI

> **Core CCNA lab** · **Platform:** switch with supported features; Packet Tracer support can be incomplete.

## Objective
Identify trusted DHCP/ARP uplinks and protect client access ports.

## Topology
`DHCP server/router — SW1 Fa0/24 (trusted)` and `PC1 — SW1 Fa0/1 (untrusted)` in VLAN 10.

## Switch configuration
```cisco
enable
configure terminal
vlan 10
 name USERS
exit
ip dhcp snooping
ip dhcp snooping vlan 10
ip arp inspection vlan 10
interface fastEthernet0/24
 switchport mode access
 switchport access vlan 10
 ip dhcp snooping trust
 ip arp inspection trust
exit
interface fastEthernet0/1
 switchport mode access
 switchport access vlan 10
 no shutdown
end
write memory
```

## Verify
```cisco
show ip dhcp snooping
show ip dhcp snooping binding
show ip arp inspection
show ip arp inspection statistics
```

Set PC1 to DHCP. The trusted server replies should be accepted; the switch can build a binding table. DAI uses bindings (or explicit ACLs) to validate ARP packets.

## Troubleshooting and safety
If the switch/simulator does not recognize these commands, change to a supported lab image. Mark the **real DHCP server uplink** as trusted, not all PC ports. DAI without valid bindings can block legitimate clients. Use this in an isolated lab.

## Lesson learned
DHCP snooping blocks unauthorized server replies; DAI helps prevent forged ARP mappings.

---
[← Previous: 07 - Lab - Switch Port Security](07%20-%20Lab%20-%20Switch%20Port%20Security.md) · [Next: 09 - Wireless Authentication and Security →](09%20-%20Wireless%20Authentication%20and%20Security.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
