# OSI Model

The **Open Systems Interconnection (OSI)** model explains communication as seven logical layers. It is a troubleshooting model, not a rule that real protocols always map neatly to one layer.

| Layer | Name | Main function | Examples |
|---:|---|---|---|
| 7 | Application | Network services used by applications | HTTP, DNS, SMTP |
| 6 | Presentation | Encoding, formatting, encryption | TLS-related representation functions |
| 5 | Session | Session/dialog management | Session establishment concepts |
| 4 | Transport | Host-to-host application delivery, ports | [TCP and UDP](10%20-%20TCP%20and%20UDP.md) |
| 3 | Network | Logical addressing and routing | IPv4, IPv6, routers |
| 2 | Data Link | Framing, MAC addresses, local delivery | Ethernet, VLANs, switches |
| 1 | Physical | Transmits raw bits and signals | Copper, fibre, RF |

## Encapsulation

Application data → **TCP segment / UDP datagram** → **IP packet** → **Ethernet frame** → **bits**. The receiver removes these headers in reverse (de-encapsulation).

## Troubleshooting examples

- L1: damaged cable or disabled link.
- L2: wrong VLAN or trunk not carrying VLAN.
- L3: incorrect IP/mask/gateway or missing route.
- L4: application port unreachable or TCP handshake failing.
- L7: DNS or HTTP service issue.

> The network layer uses IP addresses; IP address assignment is typically manual, DHCP, or SLAAC (IPv6), not a function performed by the OSI layer itself.

## Related
[TCP-IP Model and Encapsulation](06%20-%20TCP-IP%20Model%20and%20Encapsulation.md) · [IPv4 Addressing](11%20-%20IPv4%20Addressing.md) · [VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md)

---
[← Previous: 04 - LAN and WAN](04%20-%20LAN%20and%20WAN.md) · [Next: 06 - TCP-IP Model and Encapsulation →](06%20-%20TCP-IP%20Model%20and%20Encapsulation.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
