# Common Mistakes and Fixes

These common lab mistakes are useful troubleshooting reminders.

| Problem | Cause | Correction |
|---|---|---|
| `%Inconsistent address and mask` on `172.16.1.0/16` | Host bits not all zero | Use `172.16.0.0/16` or `172.16.1.0/24` |
| R1/R2 stop communicating after SW2 port changes VLAN | Access ports on different VLANs | Put both on same VLAN or add proper Layer 3 path |
| OSPF `network` syntax unclear | Wildcard mask vs subnet mask | Use wildcard or exact-IP `0.0.0.0` |
| OSPF multi-area routes absent | Area mismatch/neighbors/backbone design | Verify interfaces/areas/adjacencies and Area 0 topology |
| RIP doesn't change one-router inter-VLAN pings | All VLAN networks already directly connected | Use a second router and advertise remote subnets |
| VPN fails on ISR4321 | Crypto map applied to `g0/1` instead of actual `g0/0/1` | Apply to correct WAN interface |
| `crypto isakmp policy` rejected | Simulator/image feature support | Verify `crypto ?`; use a supported image/lab platform |
| NAT table empty | No matching traffic yet | Generate traffic and re-run `show ip nat translations` |
| SVI down/down | VLAN missing or no active member | Check VLAN and live access/trunk member |
| PC can't reach other VLAN | Missing/wrong PC default gateway | Configure gateway to VLAN router/SVI IP |

## Principles
- Check config **and** observed output.
- Never assume interface names are the same across 2911 / ISR4321 / 3560.
- A lab using public-looking addresses should stay isolated; use RFC 1918 or documentation ranges in real designs.
- Compare the intended topology and mask against the active device configuration before changing commands.

## Related
[Routing Troubleshooting](../03%20-%20IP%20Connectivity/16%20-%20Routing%20Troubleshooting.md) · [Verification and Troubleshooting Commands](../07%20-%20Cisco%20IOS%20Command%20Reference/06%20-%20Verification%20and%20Troubleshooting%20Commands.md)

---

[← Main study guide](../README.md)

---
[← Previous: 04 - Questions - Services and Security](04%20-%20Questions%20-%20Services%20and%20Security.md) · [Return to main guide →](../README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
