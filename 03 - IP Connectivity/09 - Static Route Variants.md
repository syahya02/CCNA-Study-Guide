# Static Route Variants

| Type | Example (Cisco IOS) | Purpose |
|---|---|---|
| Network route | `ip route 192.168.2.0 255.255.255.0 10.0.0.2` | Reach remote subnet |
| Host route | `ip route 192.168.2.10 255.255.255.255 10.0.0.2` | Route to one host (/32) |
| Default | `ip route 0.0.0.0 0.0.0.0 10.0.0.2` | Gateway of last resort |
| Floating static | `ip route 192.168.2.0 255.255.255.0 10.0.0.3 200` | Backup route with higher AD |
| IPv6 static | `ipv6 route 2001:db8:2::/64 2001:db8:12::2` | IPv6 destination route |

**Pitfall:** `172.16.1.0 255.255.0.0` is not a valid `/16` network address; use `172.16.0.0/16` or `172.16.1.0/24` depending on the intended prefix.

```cisco
show ip route static
show ipv6 route static
show ip route
```

---
[← Previous: 08 - Lab - IPv6 Static Routes](08%20-%20Lab%20-%20IPv6%20Static%20Routes.md) · [Next: 10 - OSPF →](10%20-%20OSPF.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
