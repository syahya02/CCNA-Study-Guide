# Lab - OSPF DR BDR Election

> **Core CCNA lab** · **Platform:** Packet Tracer (OSPF broadcast Ethernet) · **Status:** Guide, not simulator-verified.

## Objective
Identify DR, BDR and DROTHER on a common LAN.

## Topology and addressing
`R1 G0/0 — SW1 — R2 G0/0` and `R3 G0/0 — SW1` (all router ports on VLAN 1).

- R1 `10.0.0.1/24`, OSPF router ID `1.1.1.1`, interface priority **100**.
- R2 `10.0.0.2/24`, OSPF router ID `2.2.2.2`, interface priority **50**.
- R3 `10.0.0.3/24`, OSPF router ID `3.3.3.3`, interface priority **0**.

## Configuration
On each router, replace the IP/router-ID/priority with its values:
```cisco
enable
configure terminal
interface gigabitEthernet0/0
 ip address 10.0.0.1 255.255.255.0
 ip ospf priority 100
 no shutdown
exit
router ospf 1
 router-id 1.1.1.1
 network 10.0.0.0 0.0.0.255 area 0
end
write memory
```

## Verify
```cisco
show ip ospf neighbor
show ip ospf interface gigabitEthernet0/0
```

**Expected:** R3 cannot be elected DR/BDR because priority is 0. R1/R2 normally become DR/BDR in some order **depending on startup/election order**; do not assume R1 automatically preempts an existing DR.

## Troubleshooting
Check identical area, subnet, timers and network type; each router must see the others on the same broadcast segment. Restarting OSPF or toggling interfaces changes the election experiment and briefly disrupts routes.

## Lesson learned
Priority affects **eligibility**, while a completed election is not normally preempted.

---
[← Previous: 12 - Lab - Single-Area OSPF](12%20-%20Lab%20-%20Single-Area%20OSPF.md) · [Next: 14 - First Hop Redundancy Protocols →](14%20-%20First%20Hop%20Redundancy%20Protocols.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
