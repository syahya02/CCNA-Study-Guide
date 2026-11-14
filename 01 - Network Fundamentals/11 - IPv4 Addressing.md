# IPv4 Addressing

An IPv4 address is **32 bits**, written as four decimal octets (`192.168.1.10`). The prefix or subnet mask defines which bits are network bits.

## Classful defaults (historical)

| Class | Traditional first octet | Default prefix |
|---|---|---|
| A | 1–126 | /8 = 255.0.0.0 |
| B | 128–191 | /16 = 255.255.0.0 |
| C | 192–223 | /24 = 255.255.255.0 |
| D | 224–239 | Multicast |
| E | 240–255 | Reserved/special |

Modern networks use **CIDR**, so the IP address class does not decide the actual subnet mask.

## Private ranges (RFC 1918)
- `10.0.0.0/8`
- `172.16.0.0/12` (172.16.0.0–172.31.255.255)
- `192.168.0.0/16`

## Special cases
- `127.0.0.0/8`: loopback, commonly `127.0.0.1`.
- `169.254.0.0/16`: IPv4 link-local / APIPA.
- `0.0.0.0`: unspecified address; `0.0.0.0/0` represents a default route.
- `255.255.255.255`: limited broadcast.
- **All host bits 0**: subnet network address; **all host bits 1**: directed broadcast in conventional IPv4 subnets. An address ending in `.255` is **not always** a broadcast.
- `192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`: documentation/test networks.

## Example
`172.16.1.7/24` → network `172.16.1.0`, broadcast `172.16.1.255`, usual host range `.1–.254`. But `172.16.1.7/16` → network `172.16.0.0`.

## Related
[Subnetting CIDR and VLSM](13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [Binary and Subnet Quick Reference](12%20-%20Binary%20and%20Subnet%20Quick%20Reference.md) · [Routing Table and Administrative Distance](../03%20-%20IP%20Connectivity/02%20-%20Routing%20Table%20and%20Administrative%20Distance.md)

---

## Private ranges and special addresses

- `10.0.0.0/8`, `172.16.0.0/12` and `192.168.0.0/16` are private RFC 1918 ranges.
- `127.0.0.0/8` is loopback; `127.0.0.1` checks the local TCP/IP stack.
- `169.254.0.0/16` is IPv4 link-local (APIPA commonly on Windows), not an application-layer protocol.
- A final octet of `.255` is **not automatically** a broadcast address; the prefix length decides the directed broadcast.
- Class A/B/C masks are historical defaults; modern routing uses CIDR.

---
[← Previous: 10 - TCP and UDP](10%20-%20TCP%20and%20UDP.md) · [Next: 12 - Binary and Subnet Quick Reference →](12%20-%20Binary%20and%20Subnet%20Quick%20Reference.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
