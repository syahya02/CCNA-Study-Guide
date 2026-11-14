# Questions - Services and Security

**1. DNS port?**
UDP and TCP 53.

**2. What is DHCP DORA?**
Discover → Offer → Request → Acknowledge.

**3. DHCPv4 client/server ports?**
UDP 68 client, UDP 67 server.

**4. When is APIPA used?**
IPv4 link-local auto-configuration (`169.254.0.0/16`), often after DHCP failure.

**5. NTP and SNMP ports?**
NTP UDP 123; SNMP polling UDP 161; traps UDP 162.

**6. SSH vs Telnet?**
SSH encrypts management traffic (TCP 22); Telnet uses plaintext (TCP 23).

**7. What is HTTPS?**
HTTP protected by TLS; typical TCP 443 (HTTP/3 commonly UDP 443).

**8. NAT vs PAT?**
NAT rewrites address information; PAT maps many flows using transport ports/identifiers.

**9. What is the implicit ACL rule?**
Deny traffic that matches no earlier permit.

**10. What should you confirm before IPsec debugging?**
Peer reachability, routes both ways, crypto-map placement, matching selectors/policy and platform support.

**11. Does a successful VPN-lab ping prove packets were encrypted?**
No; check IPsec security association counters.

**12. What is AAA?**
Authentication, Authorization and Accounting.

**13. What are SNMP traps?**
Asynchronous notifications sent from monitored devices to a management station.

**14. Why is clock synchronization important?**
Consistent logs and security/application time-dependent operations.

## Review
[Ports and IP Protocol Numbers](../04%20-%20IP%20Services/01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md) · [NAT and PAT](../04%20-%20IP%20Services/05%20-%20NAT%20and%20PAT.md) · [Site-to-Site IPsec VPN](../05%20-%20Security%20Fundamentals/11%20-%20Site-to-Site%20IPsec%20VPN.md)

---

[← Main study guide](../README.md)

---
[← Previous: 03 - Questions - Routing](03%20-%20Questions%20-%20Routing.md) · [Next: 05 - Common Mistakes and Fixes →](05%20-%20Common%20Mistakes%20and%20Fixes.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
