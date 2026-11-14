# NAT Types and Translation Pools

NAT changes IP addresses as traffic crosses a translating device.

| Mode | Meaning | Typical use |
|---|---|---|
| Static NAT | One fixed inside-local ↔ inside-global mapping | Published internal service |
| Dynamic NAT | An inside host borrows an address from a pool | Finite pool of public addresses |
| PAT (overload) | Multiple hosts share one address using transport identifiers | Internet access |

**Inside local:** address of the inside host as seen on the internal network. **Inside global:** translated address presented outside.

```cisco
interface g0/0
 ip nat inside
interface g0/1
 ip nat outside
ip nat inside source static 192.168.10.10 203.0.113.10
ip nat pool PUBLIC 203.0.113.20 203.0.113.30 netmask 255.255.255.0
access-list 1 permit host 192.168.10.11
ip nat inside source list 1 pool PUBLIC
```

The `203.0.113.0/24` range is reserved for documentation; do not use it as real Internet-assigned addressing. Verify with `show ip nat translations` and generate matching traffic first.

## Practise this topic

- [Lab - NAT and PAT](07%20-%20Lab%20-%20NAT%20and%20PAT.md)
- [Lab - Static NAT and Dynamic NAT Pool](08%20-%20Lab%20-%20Static%20NAT%20and%20Dynamic%20NAT%20Pool.md)

---
[← Previous: 05 - NAT and PAT](05%20-%20NAT%20and%20PAT.md) · [Next: 07 - Lab - NAT and PAT →](07%20-%20Lab%20-%20NAT%20and%20PAT.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
