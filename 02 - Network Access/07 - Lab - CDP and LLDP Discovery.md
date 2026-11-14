# Lab - CDP and LLDP Discovery

> **Core CCNA lab** · **Platform:** Packet Tracer (feature support varies) · **Status:** Guide, not simulator-verified.

## Objective
Observe directly connected device names and interfaces without a topology diagram.

## Topology
`SW1 Gi0/1 --- Gi0/1 SW2`

## Steps
1. Connect two Cisco 2960 switches, name them SW1 and SW2.
2. On both switches:
```cisco
enable
configure terminal
cdp run
lldp run
interface gigabitEthernet0/1
 no shutdown
end
```
3. Inspect neighbors on SW1:
```cisco
show cdp neighbors
show cdp neighbors detail
show lldp neighbors
show lldp neighbors detail
```
4. Turn off CDP on SW1's Gi0/1 and compare:
```cisco
configure terminal
interface gigabitEthernet0/1
 no cdp enable
end
```

## Expected result
The neighbor should be listed with a local and remote port when the corresponding discovery protocol is enabled at both ends.

## Troubleshooting
Check the physical link, protocol state (`show cdp`, `show lldp`), and whether this Packet Tracer switch implements LLDP.

## Lesson learned
CDP/LLDP reveal **neighbor information**, not end-to-end connectivity.

---
[← Previous: 06 - CDP and LLDP](06%20-%20CDP%20and%20LLDP.md) · [Next: 08 - Router-on-a-Stick and SVI Routing →](08%20-%20Router-on-a-Stick%20and%20SVI%20Routing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
