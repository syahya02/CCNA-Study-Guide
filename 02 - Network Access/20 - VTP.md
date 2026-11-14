# VTP

> **Supplementary:** useful networking knowledge beyond the main CCNA v1.1 configuration objectives.

**VLAN Trunking Protocol (VTP)** can distribute VLAN database changes among Cisco switches within one VTP domain. It does **not** distribute router SVIs or enable inter-VLAN routing.

## Training modes
- **Server**: can create/update VLANs for the domain.
- **Client**: learns the VLAN database from the server (subject to version/compatibility).
- **Transparent/off**: used to avoid or restrict participation depending on platform.

## Example
```cisco
vtp domain COMPANY
vtp version 2
vtp mode server
show vtp status
```

Use the same domain/version, authentication settings (if configured), and functional trunks between participating switches.

> **Production caution:** Unexpected VTP revision/version behavior can propagate destructive VLAN database changes. Check VTP settings before attaching devices to a production domain.

## Related
[VLANs](02%20-%20VLANs.md) · [Lab - VTP Server and Client](21%20-%20Lab%20-%20VTP%20Server%20and%20Client.md)

---

## Practise this topic

- [Lab - VTP Server and Client](21%20-%20Lab%20-%20VTP%20Server%20and%20Client.md)

---
[← Previous: 19 - Lab - Wireless LAN GUI](19%20-%20Lab%20-%20Wireless%20LAN%20GUI.md) · [Next: 21 - Lab - VTP Server and Client →](21%20-%20Lab%20-%20VTP%20Server%20and%20Client.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
