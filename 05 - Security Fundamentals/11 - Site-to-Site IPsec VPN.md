# Site-to-Site IPsec VPN

> **Supplementary:** useful networking knowledge beyond the main CCNA v1.1 configuration objectives.

**IPsec** protects traffic between networks across an untrusted link. In the supplied Cisco example, two routers use an **IKEv1 policy**, pre-shared keys, an IPsec transform set, an ACL selecting interesting traffic, and a crypto map on the WAN interface.

## Conceptual steps
1. Verify ordinary IP reachability and routing between peers/LANs.
2. Negotiate an IKE security association (Phase 1 in IKEv1).
3. Negotiate IPsec SAs / traffic selectors (Phase 2).
4. Protect traffic matching the crypto ACL.
5. Check negotiation state and encryption/decryption counters.

## Example fragments (legacy training syntax)
```cisco
crypto isakmp policy 10
 encryption aes 256
 hash sha
 authentication pre-share
 group 14
! Configure a real, unique strong secret, not a public example
crypto isakmp key <lab-only-secret> address 10.0.0.2
crypto ipsec transform-set VPN-SET esp-aes 256 esp-sha-hmac
access-list 110 permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255
crypto map VPN-MAP 10 ipsec-isakmp
 set peer 10.0.0.2
 set transform-set VPN-SET
 match address 110
interface g0/0/1
 crypto map VPN-MAP
```

**Packet Tracer limitations:** some simulated routers do not offer `crypto isakmp`; DH groups and algorithms vary by image. `group 1` is insecure/obsolete and must not be a production fallback. Prefer modern IKEv2 and approved strong cryptography in real environments.

## Verify
```cisco
show crypto isakmp sa
show crypto ipsec sa
show crypto map
show access-lists
```

## Related
[ACLs](04%20-%20ACLs.md) · [Static and Default Routing](../03%20-%20IP%20Connectivity/04%20-%20Static%20and%20Default%20Routing.md) · [Lab - Site-to-Site IPsec VPN](12%20-%20Lab%20-%20Site-to-Site%20IPsec%20VPN.md)

---

## Practise this topic

- [Lab - Site-to-Site IPsec VPN](12%20-%20Lab%20-%20Site-to-Site%20IPsec%20VPN.md)

---
[← Previous: 10 - Lab - WPA2 Wireless Client](10%20-%20Lab%20-%20WPA2%20Wireless%20Client.md) · [Next: 12 - Lab - Site-to-Site IPsec VPN →](12%20-%20Lab%20-%20Site-to-Site%20IPsec%20VPN.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
