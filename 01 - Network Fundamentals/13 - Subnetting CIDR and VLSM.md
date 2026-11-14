# Subnetting CIDR and VLSM

**Subnetting** divides a network into smaller prefixes. **CIDR** uses slash notation (`/26`), specifying the count of leading 1 bits in the mask. **VLSM** uses different prefix lengths for networks of different sizes.

## Worked example: 192.168.10.0/26

- Mask: `255.255.255.192`.
- Block size: `256 − 192 = 64` in the last octet.
- Subnet starts: `.0`, `.64`, `.128`, `.192`.
- First subnet: network `.0`, host `.1–.62`, broadcast `.63`.
- Total addresses: 64; conventional usable hosts: 62.

## Four-step method

1. Identify required hosts and choose a prefix.
2. Find the interesting octet (first mask octet other than 255/0).
3. Calculate block size `256 − mask octet` and align the network address.
4. Determine network, first/last hosts and broadcast.

## Static-route mistake from training

```cisco
! Invalid: 172.16.1.0 contains host bits for a /16 network
ip route 172.16.1.0 255.255.0.0 1.1.1.1
! Correct /16 network
ip route 172.16.0.0 255.255.0.0 1.1.1.1
! Or correct /24 route
ip route 172.16.1.0 255.255.255.0 1.1.1.1
```

## Legacy note: subnet zero
Old material may mention the `ip subnet-zero` command. Modern Cisco IPv4 subnetting normally permits the all-zero and all-ones subnets; do not treat them as invalid.

## Related
[Binary and Subnet Quick Reference](12%20-%20Binary%20and%20Subnet%20Quick%20Reference.md) · [IPv4 Addressing](11%20-%20IPv4%20Addressing.md) · [Static and Default Routing](../03%20-%20IP%20Connectivity/04%20-%20Static%20and%20Default%20Routing.md)

---

## Practise this topic

- [Lab - IPv4 Subnetting Practice](14%20-%20Lab%20-%20IPv4%20Subnetting%20Practice.md)
- [Lab - Basic Router Interfaces](15%20-%20Lab%20-%20Basic%20Router%20Interfaces.md)

---
[← Previous: 12 - Binary and Subnet Quick Reference](12%20-%20Binary%20and%20Subnet%20Quick%20Reference.md) · [Next: 14 - Lab - IPv4 Subnetting Practice →](14%20-%20Lab%20-%20IPv4%20Subnetting%20Practice.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
