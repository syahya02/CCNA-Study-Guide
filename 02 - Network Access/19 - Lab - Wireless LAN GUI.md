# Lab - Wireless LAN GUI

> **Core CCNA GUI exercise** · **Platform:** Packet Tracer wireless router/AP or WLC-supported topology · **Status:** Menu paths vary by version.

## Objective
Create an SSID, apply WPA2-Personal/AES and connect a wireless client.

## Topology
`Wireless client )) AP / wireless router --- switch --- (optional PC or server)`

## Steps
1. Add a compatible wireless AP/router and wireless laptop/PC in Packet Tracer.
2. In the device **Config or GUI** tab, create SSID `CCNA-LAB` and configure **WPA2-PSK (AES)** with a strong unique *lab-only* password.
3. Confirm the LAN addressing/DHCP pool provided by the router or server.
4. On the laptop, select the SSID, authenticate, and obtain an IP address.
5. Ping the local default gateway; inspect association status and network settings.

## Verification
Check associated client, SSID, security mode, IP/mask/gateway and signal. From the client run `ipconfig` and `ping <gateway>`.

## Troubleshooting
Wrong PSK, WPA mode mismatch, missing DHCP service, wrong VLAN/SSID mapping and weak signal are common causes.

## Lesson learned
An SSID identifies a wireless network; **authentication/encryption and VLAN/IP configuration** determine whether a client can connect and pass traffic.

---
[← Previous: 18 - Wireless Architectures and WLC](18%20-%20Wireless%20Architectures%20and%20WLC.md) · [Next: 20 - VTP →](20%20-%20VTP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
