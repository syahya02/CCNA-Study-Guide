# Lab - Switch Port Security

> **Core CCNA lab** · **Platform:** Cisco 2960 Packet Tracer · **Status:** Guide, not simulator-verified.

## Objective
Restrict a switch access port to an expected endpoint MAC address.

## Topology
`PC1 — SW1 Fa0/1`, optional `PC2` to test violation.

## SW1 configuration
```cisco
enable
configure terminal
hostname SW1
interface fastEthernet0/1
 switchport mode access
 switchport access vlan 10
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation restrict
 no shutdown
exit
end
write memory
```

Create VLAN 10 first if it does not exist:
```cisco
conf t
vlan 10
 name USERS
end
```

## Verify and test
1. Send traffic from PC1 so its MAC can be learned.
2. On SW1:
```cisco
show port-security interface fastEthernet0/1
show port-security address
show mac address-table
```
3. Replace PC1 with PC2 or spoof another MAC in an isolated lab. Inspect violation counters.

## Troubleshooting
Port security requires a supported **access** port; do not apply this recipe to trunks. For `restrict`, violating frames are dropped and counters increase; for `shutdown`, the port can become err-disabled.

## Lesson learned
Port security limits endpoint MAC usage; it does not replace authentication such as 802.1X.

---
[← Previous: 06 - Layer 2 Security and AAA](06%20-%20Layer%202%20Security%20and%20AAA.md) · [Next: 08 - Lab - DHCP Snooping and DAI →](08%20-%20Lab%20-%20DHCP%20Snooping%20and%20DAI.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
