# Lab - IPv4 Subnetting Practice

> **Core CCNA practice** · **Platform:** Packet Tracer and manual calculation · **Status:** Guide, not simulator-verified.

## Objective
Calculate usable ranges and configure two PCs in a subnet without relying on the address class.

## Topology
```text
PC1 --- SW1 --- PC2
```

## Addressing plan
Start with `192.168.40.0/24`. Divide it into **four equal /26 subnets**:

| Subnet | Network | Usable hosts | Broadcast |
|---|---|---|---|
| 1 | `192.168.40.0/26` | `.1`–`.62` | `.63` |
| 2 | `192.168.40.64/26` | `.65`–`.126` | `.127` |
| 3 | `192.168.40.128/26` | `.129`–`.190` | `.191` |
| 4 | `192.168.40.192/26` | `.193`–`.254` | `.255` |

**Step 1.** Connect two PCs to a 2960 switch.

**Step 2.** On PC1 configure `192.168.40.65` / `255.255.255.192`; on PC2 configure `192.168.40.66` with the same mask. No gateway is necessary to ping within the same subnet.

**Step 3.** From PC1 run:
```text
ping 192.168.40.66
ipconfig
```

**Step 4.** Change PC2 to `192.168.40.130/26`. The direct ping should now fail because the PCs are in different subnets with no router.

## Verification and troubleshooting
Confirm both masks, host ranges, cabling and switchport status. To connect different subnets, add a Layer 3 gateway; changing a mask alone does not provide routing.

## Lesson learned
A subnet's prefix determines its network and broadcast addresses; the old A/B/C class is not the routing boundary.

---
[← Previous: 13 - Subnetting CIDR and VLSM](13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [Next: 15 - Lab - Basic Router Interfaces →](15%20-%20Lab%20-%20Basic%20Router%20Interfaces.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
