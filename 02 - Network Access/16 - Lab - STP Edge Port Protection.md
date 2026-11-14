# Lab - STP Edge Port Protection

> **Core CCNA extension** · **Platform:** Packet Tracer; support varies · **Status:** Guide, not simulator-verified.

## Objective
Protect a PC-facing access port from an unexpected switch connection.

## Topology
`PC1 --- SW1 Fa0/10` then replace PC1 with `SW2 --- SW1 Fa0/10` for the test.

## SW1 configuration
```cisco
enable
configure terminal
hostname SW1
spanning-tree mode rapid-pvst
vlan 10
 name USERS
exit
interface fastEthernet0/10
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown
end
write memory
```

## Test
1. Confirm the PC can communicate normally.
2. Disconnect PC1; connect SW2 to SW1 Fa0/10. The port should enter err-disabled when BPDUs arrive (if supported).
3. Inspect status and logs; remove SW2 before recovering the interface.

```cisco
show interfaces status
show spanning-tree vlan 10
show logging
```

## Recovery
```cisco
configure terminal
interface fastEthernet0/10
 shutdown
 no shutdown
end
```

## Troubleshooting
If Packet Tracer does not simulate the protection behaviour, learn the command and verify the configuration rather than inferring a real-world outcome.

## Lesson learned
PortFast/BPDU Guard are **edge-port protections**; do not place them indiscriminately on normal inter-switch links.

---
[← Previous: 15 - Lab - Layer 3 EtherChannel](15%20-%20Lab%20-%20Layer%203%20EtherChannel.md) · [Next: 17 - Wireless Networking Basics →](17%20-%20Wireless%20Networking%20Basics.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
