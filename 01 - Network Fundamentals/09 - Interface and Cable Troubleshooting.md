# Interface and Cable Troubleshooting

## First checks
1. **Physical link:** cable, SFP, LEDs, admin state (`no shutdown`).
2. **Speed and duplex:** both ends compatible; a duplex mismatch can cause late collisions, CRCs and poor throughput.
3. **Counters:** CRC/frame errors, drops, collisions and interface resets.
4. **Layer 2:** VLAN assignment, trunk mode, allowed VLANs, STP state.
5. **Layer 3:** IP, subnet mask, default gateway, routing table.

```cisco
show interfaces status
show interfaces gigabitEthernet 0/1
show ip interface brief
show logging
```

**Copper** is common for short Ethernet runs; **single-mode fibre** is suited to longer-distance optical links; **multimode** is commonly used for shorter optical runs. Cable lengths and optics must match the hardware specifications.

### Try it
Disable a switch port and verify `administratively down`, then restore it with `no shutdown`. Check counters before and after. Use [Lab - Basic Router Interfaces](15%20-%20Lab%20-%20Basic%20Router%20Interfaces.md) for initial CLI practice.

---
[← Previous: 08 - Ethernet and Cabling](08%20-%20Ethernet%20and%20Cabling.md) · [Next: 10 - TCP and UDP →](10%20-%20TCP%20and%20UDP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
