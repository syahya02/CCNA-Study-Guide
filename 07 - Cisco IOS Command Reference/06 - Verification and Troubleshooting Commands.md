# Verification and Troubleshooting Commands

| Command | Question it answers |
|---|---|
| `show ip interface brief` | Is the interface up/up and addressed? |
| `show interfaces g0/0` | Any physical errors/duplex issues? |
| `show ip route` | Where will packets go? |
| `show ipv6 route` | Where will IPv6 packets go? |
| `show cdp neighbors` | Which Cisco device is connected? |
| `show lldp neighbors` | Which LLDP device is connected? |
| `show vlan brief` | Which VLANs/access ports exist? |
| `show interfaces trunk` | Which VLANs cross trunks? |
| `show mac address-table` | Which ports learned destination MACs? |
| `show ip protocols` | What routing protocols run? |
| `show ip ospf neighbor` | Are OSPF adjacencies formed? |
| `show ip eigrp neighbors` | Are EIGRP adjacencies formed? |
| `show ip nat translations` | Did NAT translate traffic? |
| `show access-lists` | Are ACLs matching packets? |
| `show crypto isakmp sa` | Did IKEv1 negotiate? |
| `show crypto ipsec sa` | Are packets being encrypted/decrypted? |
| `ping ADDRESS` | Is a destination responding to ICMP? |
| `traceroute ADDRESS` | Which responding hops are visible? |

## Five-minute troubleshooting sequence
1. Physical link → VLAN/trunk → IP/mask/gateway.
2. Neighbor link ping → route → reverse route.
3. Routing protocol neighbors or ACL/NAT/VPN specifics.
4. Save working configuration and record the expected/actual output.

## Related
[Routing Troubleshooting](../03%20-%20IP%20Connectivity/16%20-%20Routing%20Troubleshooting.md) · [Network Foundations](../01%20-%20Network%20Fundamentals/01%20-%20Network%20Foundations.md) · [Lab - Multi-Area OSPF](../03%20-%20IP%20Connectivity/23%20-%20Lab%20-%20Multi-Area%20OSPF.md)

---

[← Main study guide](../README.md)

---
[← Previous: 05 - NAT ACL and VPN Commands](05%20-%20NAT%20ACL%20and%20VPN%20Commands.md) · [Next chapter: 08 - Revision and Practice Questions →](../08%20-%20Revision%20and%20Practice%20Questions/README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
