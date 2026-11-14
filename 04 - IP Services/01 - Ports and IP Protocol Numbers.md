# Ports and IP Protocol Numbers

**TCP/UDP port numbers** identify applications at Layer 4. **IP protocol numbers** identify the next protocol directly inside an IP packet. They are **not the same namespace**.

## Common ports
| Service | Transport | Port |
|---|---|---|
| FTP control | TCP | 21 (FTP data often TCP 20 in active mode) |
| SSH / SFTP | TCP | 22 |
| Telnet | TCP | 23 |
| SMTP | TCP | 25 |
| DNS | UDP/TCP | 53 |
| DHCPv4 server/client | UDP | 67 / 68 |
| TFTP | UDP | 69 |
| HTTP | TCP | 80 |
| POP3 | TCP | 110 |
| NTP | UDP | 123 |
| IMAP | TCP | 143 |
| SNMP poll/trap | UDP | 161 / 162 |
| HTTPS | TCP | 443 (HTTP/3 uses UDP 443) |

## IPv4 protocol numbers
| Protocol | IP protocol number |
|---|---:|
| ICMP | 1 |
| IP-in-IP | 4 |
| TCP | 6 |
| UDP | 17 |
| IPv6 encapsulated | 41 |
| GRE | 47 |
| EIGRP | 88 |
| OSPF | 89 |
| L2TP | 115 |

> Correction from screenshot: DNS uses **UDP and TCP 53**. OSPF uses IP protocol 89, **not** TCP port 89.

## Related
[TCP and UDP](../01%20-%20Network%20Fundamentals/10%20-%20TCP%20and%20UDP.md) · [DNS](02%20-%20DNS.md) · [DHCP](03%20-%20DHCP.md) · [NTP and SNMP Syslog](09%20-%20NTP%20and%20SNMP%20Syslog.md)

---
[← Chapter study path](README.md) · [Next: 02 - DNS →](02%20-%20DNS.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
