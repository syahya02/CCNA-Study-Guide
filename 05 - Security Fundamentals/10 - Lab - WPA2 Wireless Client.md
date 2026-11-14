# Lab - WPA2 Wireless Client

> **Core CCNA GUI lab** · **Platform:** Packet Tracer; device menus vary by release.

## Objective
Connect a wireless client to a secured WLAN and confirm Layer 3 connectivity.

## Topology
`Wireless Laptop )) Wireless Router/AP — (wired router or local switch)`

## Steps
1. Set the WLAN SSID to `CCNA-SECURE` and security to **WPA2-Personal (AES)**.
2. Configure a unique strong lab PSK, and ensure the LAN DHCP scope is active.
3. On the laptop, choose `CCNA-SECURE` and provide the PSK.
4. Confirm the laptop receives an IPv4 address, mask, gateway and DNS information.
5. Ping the gateway and another device if one is present.

## Verify
Inspect associated clients, encryption mode, channel/SSID and client IP configuration. Repeat with a deliberately incorrect PSK and note association failure.

## Troubleshooting
Check SSID spelling, password, WPA mode, wireless adapter presence, DHCP scope, client distance and WLAN-to-VLAN mapping on WLC-based designs.

## Lesson learned
Authentication/security must succeed before the client can receive normal routed connectivity.

---
[← Previous: 09 - Wireless Authentication and Security](09%20-%20Wireless%20Authentication%20and%20Security.md) · [Next: 11 - Site-to-Site IPsec VPN →](11%20-%20Site-to-Site%20IPsec%20VPN.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
