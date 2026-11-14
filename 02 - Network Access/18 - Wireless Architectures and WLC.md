# Wireless Architectures and WLC

## Common arrangements
- **Autonomous AP:** configured individually; locally manages WLAN settings.
- **Controller-based AP:** managed through a Wireless LAN Controller (WLC) over a control connection (commonly CAPWAP).
- **Cloud-managed:** policies and visibility are managed through a hosted controller or dashboard.

## Infrastructure connections
APs may connect to access ports or trunks depending on the architecture. A WLC connects to the wired network using appropriate ports/LAGs; client VLAN and management mapping must agree with the design.

## GUI study checklist
Find and interpret the WLAN/SSID, WLAN-to-VLAN mapping, WPA2/WPA3 security, QoS profile, AP association, client list and DHCP status. Menu names vary by WLC and simulator version.

## Practise this topic

- [Lab - Wireless LAN GUI](19%20-%20Lab%20-%20Wireless%20LAN%20GUI.md)

---
[← Previous: 17 - Wireless Networking Basics](17%20-%20Wireless%20Networking%20Basics.md) · [Next: 19 - Lab - Wireless LAN GUI →](19%20-%20Lab%20-%20Wireless%20LAN%20GUI.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
