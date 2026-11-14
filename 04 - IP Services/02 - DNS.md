# DNS

**Domain Name System** resolves names to records, such as an IPv4 **A** address or IPv6 **AAAA** address. Common DNS transports: **UDP 53** and **TCP 53** (e.g. large responses/zone transfers).

## Resolution simplified

1. User requests `www.example.com`.
2. Client sends a query to its configured **recursive resolver**.
3. If not cached, the resolver uses root, TLD and authoritative DNS as required.
4. The resolver returns a response and caches it according to TTL.

The resolver, not usually the desktop client, performs iterative queries to root/authoritative servers.

## Important records
| Type | Meaning |
|---|---|
| A / AAAA | IPv4 / IPv6 address |
| CNAME | Alias to another name |
| MX | Mail destination |
| NS | Delegated authoritative DNS servers |
| PTR | Reverse lookup |
| TXT | Arbitrary text (often verification/security records) |

## Verify
Windows: `nslookup example.com`; Linux/macOS: `dig example.com` where installed.

## Related
[DHCP](03%20-%20DHCP.md) · [Ports and IP Protocol Numbers](01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md) · [TCP and UDP](../01%20-%20Network%20Fundamentals/10%20-%20TCP%20and%20UDP.md)

---
[← Previous: 01 - Ports and IP Protocol Numbers](01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md) · [Next: 03 - DHCP →](03%20-%20DHCP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
