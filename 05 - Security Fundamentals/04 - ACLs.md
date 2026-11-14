# ACLs

**Access Control Lists** test packets against ordered rules. Rules are checked **top to bottom**, first match wins, with an **implicit deny** at the end.

## Standard vs extended
- **Standard IPv4 ACL**: match source IPv4 only (numbered 1–99, 1300–1999).
- **Extended IPv4 ACL**: source, destination, protocol, ports (100–199, 2000–2699).

## Standard ACL example
```cisco
access-list 1 deny host 192.168.10.10
access-list 1 permit any
interface g0/0
 ip access-group 1 in
```

## Extended ACL example
```cisco
ip access-list extended ALLOW-WEB
 permit tcp 192.168.10.0 0.0.0.255 any eq 443
 deny ip any any log
interface g0/1
 ip access-group ALLOW-WEB out
```

## Wildcard masks
- `/24` subnet mask `255.255.255.0` → wildcard `0.0.0.255`.
- `host 192.168.10.10` is shorthand for `192.168.10.10 0.0.0.0`.

## Verify
```cisco
show access-lists
show ip interface g0/0
```

## Related
[Subnetting CIDR and VLSM](../01%20-%20Network%20Fundamentals/13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [Site-to-Site IPsec VPN](11%20-%20Site-to-Site%20IPsec%20VPN.md) · [Lab - Serial WAN and ACLs](../03%20-%20IP%20Connectivity/25%20-%20Lab%20-%20Serial%20WAN%20and%20ACLs.md)

---

## Practise this topic

- [Lab - Extended ACL Practice](05%20-%20Lab%20-%20Extended%20ACL%20Practice.md)

---
[← Previous: 03 - Lab - Secure Cisco Device with SSH](03%20-%20Lab%20-%20Secure%20Cisco%20Device%20with%20SSH.md) · [Next: 05 - Lab - Extended ACL Practice →](05%20-%20Lab%20-%20Extended%20ACL%20Practice.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
