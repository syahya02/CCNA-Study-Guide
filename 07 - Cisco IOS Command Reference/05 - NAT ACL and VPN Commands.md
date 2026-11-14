# NAT ACL and VPN Commands

## ACL example
```cisco
access-list 1 permit 192.168.1.0 0.0.0.255
ip access-list extended WEB
 permit tcp any host 192.168.20.10 eq 443
interface g0/0
 ip access-group WEB in
```

## NAT / PAT
```cisco
interface g0/0
 ip nat inside
interface g0/1
 ip nat outside
ip nat inside source list 1 interface g0/1 overload
show ip nat translations
show ip nat statistics
```

## IKEv1/IPsec (legacy lab)
```cisco
crypto isakmp policy 10
crypto ipsec transform-set VPN-SET esp-aes 256 esp-sha-hmac
crypto map VPN-MAP 10 ipsec-isakmp
show crypto isakmp sa
show crypto ipsec sa
```

**Caution:** IKEv1 commands and algorithms depend on IOS / Packet Tracer capabilities; this is a training reference, not a modern hardened configuration.

## Related
[ACLs](../05%20-%20Security%20Fundamentals/04%20-%20ACLs.md) · [NAT and PAT](../04%20-%20IP%20Services/05%20-%20NAT%20and%20PAT.md) · [Site-to-Site IPsec VPN](../05%20-%20Security%20Fundamentals/11%20-%20Site-to-Site%20IPsec%20VPN.md)

---

[← Main study guide](../README.md)

---
[← Previous: 04 - Routing Commands](04%20-%20Routing%20Commands.md) · [Next: 06 - Verification and Troubleshooting Commands →](06%20-%20Verification%20and%20Troubleshooting%20Commands.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
