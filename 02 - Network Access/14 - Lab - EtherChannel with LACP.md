# Lab - EtherChannel with LACP

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective

Bundle two physical Ethernet links into **one logical EtherChannel (Port-channel 1)** using **LACP**. Verify both links participate and demonstrate link redundancy.

**Concept:** [STP and EtherChannel](11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md) · [VLANs](02%20-%20VLANs.md)

## 1. Devices and cabling

- 2 × Cisco **2960-24TT** switches: SW1 and SW2
- 2 × PC-PT devices: PC1 and PC2
- Use the **Automatic Connection** tool or suitable Ethernet cables.

```text
 PC1                           PC2
  |                             |
Fa0/10                       Fa0/10
  |                             |
 SW1 == Fa0/1 ----- Fa0/1 == SW2
     \_ Fa0/2 ----- Fa0/2 _/
           Port-channel 1
           (LACP bundle)
```

| Link | SW1 | SW2 |
|---|---|---|
| EtherChannel member 1 | Fa0/1 | Fa0/1 |
| EtherChannel member 2 | Fa0/2 | Fa0/2 |
| PC connections | PC1 → Fa0/10 | PC2 → Fa0/10 |

**Important:** Connect both links between the **same two switches**. Do not connect one EtherChannel member to a different independent switch.

## 2. Address the PCs

| Device | IP address | Subnet mask | Gateway |
|---|---|---|---|
| PC1 | `192.168.10.10` | `255.255.255.0` | Not required for same-VLAN test |
| PC2 | `192.168.10.20` | `255.255.255.0` | Not required for same-VLAN test |

Both PC-facing access ports use **VLAN 10**. The EtherChannel will carry VLAN 10 as an **802.1Q trunk**.

## 3. Configure SW1

```cisco
enable
configure terminal
hostname SW1
vlan 10
 name HR
exit
interface range fastEthernet 0/1 - 2
 switchport mode trunk
 channel-group 1 mode active
 no shutdown
exit
interface port-channel 1
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
exit
interface fastEthernet 0/10
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
exit
end
write memory
```

**Why:** `channel-group 1 mode active` starts LACP negotiation on both Fa0/1 and Fa0/2. `interface port-channel 1` configures the combined logical trunk.

## 4. Configure SW2

```cisco
enable
configure terminal
hostname SW2
vlan 10
 name HR
exit
interface range fastEthernet 0/1 - 2
 switchport mode trunk
 channel-group 1 mode active
 no shutdown
exit
interface port-channel 1
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
exit
interface fastEthernet 0/10
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
exit
end
write memory
```

> Configure **matching settings on both ends**: member speed/duplex, switchport mode, VLANs, native VLAN and allowed VLANs. Avoid changing member-port settings independently after forming the bundle.

## 5. Verify EtherChannel

Run on **both switches**:

```cisco
show etherchannel summary
show interfaces trunk
show spanning-tree vlan 10
show running-config
```

A healthy LACP bundle commonly looks similar to:

```text
Group  Port-channel  Protocol  Ports
1      Po1(SU)       LACP      Fa0/1(P) Fa0/2(P)
```

- `Po1` = logical Port-channel 1
- `(S)` = Layer 2 EtherChannel
- `(U)` = in use
- `(P)` = physical interface bundled in the port-channel

The exact output may vary by Packet Tracer version. You should see **Po1** as the inter-switch trunk rather than independent forwarding trunks for the two member ports.

## 6. Test connectivity and redundancy

From **PC1**, ping PC2:

```text
ping 192.168.10.20
```

Then temporarily disable **one member** on SW1:

```cisco
enable
configure terminal
interface fastEthernet 0/2
 shutdown
end
```

Check:

```cisco
show etherchannel summary
```

`Po1` should remain operational with Fa0/1 as its remaining active member. The PC-to-PC ping should continue working (a brief interruption may occur during convergence).

Restore the member:

```cisco
configure terminal
interface fastEthernet 0/2
 no shutdown
end
write memory
```

Check again for **both** member ports marked `(P)`.

## 7. Troubleshooting

| Symptom | Check |
|---|---|
| `Po1` down or suspended | Ensure LACP is compatible: active/active or active/passive; **passive/passive fails** |
| One member missing `(P)` | Cable, interface status, speed/duplex and switchport/trunk consistency |
| Trunk VLAN missing | `show interfaces trunk`; check Port-channel allowed VLAN list |
| Ping fails | PC IP/mask, VLAN 10 access ports, MAC learning, LACP state |
| Switchports blocked by STP | Check `show spanning-tree vlan 10`; STP sees a properly formed Port-channel as **one logical link** |

## 8. Lesson learned

**EtherChannel combines compatible physical links into one logical link**, providing redundancy and aggregate capacity across multiple traffic flows. A single flow typically uses **one** member link according to the hashing policy; do not expect one flow to automatically double in speed.

**STP vs EtherChannel:** [Lab - STP Redundant Links](12%20-%20Lab%20-%20STP%20Redundant%20Links.md) shows how STP blocks a redundant path to prevent loops. EtherChannel instead makes multiple links act as one logical connection. The technologies can operate together.

**Related:** [STP and EtherChannel](11%20-%20Spanning%20Tree%20Protocol%20and%20Rapid%20PVST+.md) · [Lab - STP Redundant Links](12%20-%20Lab%20-%20STP%20Redundant%20Links.md) · [Lab - VLANs and Trunks](04%20-%20Lab%20-%20VLANs%20and%20Trunks.md) · [VLANs](02%20-%20VLANs.md)

**Cisco reference:** [Configuring EtherChannels — Catalyst 2960](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/12-2_58_se/configuration/guide/2960scg/swethchl.html)

---
[← Previous: 13 - EtherChannel and LACP](13%20-%20EtherChannel%20and%20LACP.md) · [Next: 15 - Lab - Layer 3 EtherChannel →](15%20-%20Lab%20-%20Layer%203%20EtherChannel.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
