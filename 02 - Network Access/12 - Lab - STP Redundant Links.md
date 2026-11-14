# Lab - STP Redundant Links

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective

Build a **Layer 2 triangle**, observe how STP prevents a switching loop, choose the root bridge, and confirm that a backup path is activated when an active link fails.

**Concept:** [STP and EtherChannel](11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md) · [VLANs](02%20-%20VLANs.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md)

## 1. Devices and cabling

- 3 × **Cisco 2960-24TT** switches: SW1, SW2, SW3
- 2 × **PC-PT** devices: PC1, PC2
- Connect cables using Packet Tracer's **Automatic Connection** tool or appropriate Ethernet cables.

```text
            SW1 (root bridge)
           /   \
   Fa0/1  /     \  Fa0/2
         /       \
  Fa0/1 SW2-------SW3 Fa0/1
         Fa0/2  Fa0/2
         |         |
       Fa0/10    Fa0/10
         |         |
        PC1       PC2
```

| Link | Interface A | Interface B |
|---|---|---|
| SW1 ↔ SW2 | SW1 Fa0/1 | SW2 Fa0/1 |
| SW1 ↔ SW3 | SW1 Fa0/2 | SW3 Fa0/1 |
| SW2 ↔ SW3 | SW2 Fa0/2 | SW3 Fa0/2 |
| PC1 ↔ SW2 | PC1 FastEthernet0 | SW2 Fa0/10 |
| PC2 ↔ SW3 | PC2 FastEthernet0 | SW3 Fa0/10 |

All three switches use **VLAN 10 (HR)**. Links **between switches** are trunks.

## 2. Configure PC addresses

| Device | IP address | Subnet mask | Gateway |
|---|---|---|---|
| PC1 | `192.168.10.10` | `255.255.255.0` | Not required for same-VLAN test |
| PC2 | `192.168.10.20` | `255.255.255.0` | Not required for same-VLAN test |

Packet Tracer: PC → **Desktop → IP Configuration**.

## 3. Configure SW1 (root bridge)

```cisco
enable
configure terminal
hostname SW1
spanning-tree mode rapid-pvst
vlan 10
 name HR
exit
interface range fastEthernet 0/1 - 2
 switchport mode trunk
 no shutdown
exit
spanning-tree vlan 10 root primary
end
write memory
```

**Why:** `root primary` makes SW1 the intended root bridge for VLAN 10. `rapid-pvst` runs Cisco's rapid per-VLAN spanning tree.

## 4. Configure SW2 (secondary root)

```cisco
enable
configure terminal
hostname SW2
spanning-tree mode rapid-pvst
vlan 10
 name HR
exit
interface range fastEthernet 0/1 - 2
 switchport mode trunk
 no shutdown
exit
interface fastEthernet 0/10
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown
exit
spanning-tree vlan 10 root secondary
end
write memory
```

**Why:** SW2 is the intended backup root for VLAN 10. **PortFast and BPDU Guard belong on the PC-facing access port only**, not on inter-switch trunks.

## 5. Configure SW3

```cisco
enable
configure terminal
hostname SW3
spanning-tree mode rapid-pvst
vlan 10
 name HR
exit
interface range fastEthernet 0/1 - 2
 switchport mode trunk
 no shutdown
exit
interface fastEthernet 0/10
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown
exit
end
write memory
```

## 6. Observe STP

Run on **all three switches**:

```cisco
show spanning-tree vlan 10
show interfaces trunk
show vlan brief
```

**Expected observations (exact port depends on topology/costs):**

- **SW1** reports itself as the root for VLAN 10.
- Some redundant inter-switch path is put into a **non-forwarding** state (typically `Altn/BLK` or `Altn/DISC`, depending on STP mode/output).
- In this equal-speed topology, SW3's link to SW2 will typically be the alternate path because SW2 has a better bridge ID.
- All three links can show physical **up**, even though STP intentionally prevents forwarding on one path.

> An amber/orange link indication in Packet Tracer may represent a non-forwarding STP port. Check `show spanning-tree vlan 10` rather than judging by colour alone.

## 7. Test communication and link failure

On **PC1 → Command Prompt**:

```text
ping 192.168.10.20
```

The two PCs should communicate inside VLAN 10 even though the switches have a physical loop.

Now simulate a failure on **SW1**:

```cisco
enable
configure terminal
interface fastEthernet 0/2
 shutdown
end
```

Wait for STP to reconverge, then run on **SW3**:

```cisco
show spanning-tree vlan 10
```

Ping PC2 from PC1 again. The SW2↔SW3 path should now carry traffic. Restore the link:

```cisco
SW1# configure terminal
SW1(config)# interface fastEthernet 0/2
SW1(config-if)# no shutdown
SW1(config-if)# end
SW1# write memory
```

## 8. Troubleshooting

| Symptom | Check |
|---|---|
| Ping fails | PC IP/mask, access VLAN 10, physical cables, and STP convergence |
| SW1 is not root | `show spanning-tree vlan 10`; check that `root primary` was configured on SW1 |
| No trunk | `show interfaces trunk`; both ends must be compatible |
| Access port disabled / err-disabled | Confirm PortFast/BPDU Guard applied to PC ports only; inspect interface status |
| Wrong port is alternate | STP chooses using path cost and bridge/port IDs; blocking location can vary |

## 9. Lesson learned

**STP prevents Layer 2 loops by keeping redundant links available but non-forwarding until needed.** It does not combine bandwidth from separate physical links; for that see [Lab - EtherChannel with LACP](14%20-%20Lab%20-%20EtherChannel%20with%20LACP.md).

**Related:** [STP and EtherChannel](11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md) · [Switching and MAC Learning](01%20-%20Switching%20and%20MAC%20Learning.md) · [Lab - VLANs and Trunks](04%20-%20Lab%20-%20VLANs%20and%20Trunks.md) · [Lab - EtherChannel with LACP](14%20-%20Lab%20-%20EtherChannel%20with%20LACP.md)

**Cisco reference:** [Configuring STP — Catalyst 2960](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/12-2_58_se/configuration/guide/2960scg/swstp.html)

---
[← Previous: 11 - Spanning Tree Protocol and Rapid PVST+](11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md) · [Next: 13 - EtherChannel and LACP →](13%20-%20EtherChannel%20and%20LACP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
