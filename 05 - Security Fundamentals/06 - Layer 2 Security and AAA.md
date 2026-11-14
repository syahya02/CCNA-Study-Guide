# Layer 2 Security and AAA

## Common controls
- **Port security**: limit/learn permitted MAC addresses on access ports; optionally shut down on violations.
- **DHCP snooping**: distinguish trusted DHCP-server-facing ports and untrusted client ports.
- **Dynamic ARP Inspection (DAI)**: validate ARP traffic using trusted binding information.
- **BPDU Guard**: protects access ports against unintended STP topology changes.

## AAA
- **Authentication**: who are you?
- **Authorization**: what may you do?
- **Accounting**: what did you do?
- **RADIUS/TACACS+**: centralised authentication/authorization/accounting integration.

## Port security example
```cisco
interface fa0/1
 switchport mode access
 switchport port-security
 switchport port-security maximum 2
 switchport port-security violation restrict
show port-security interface fa0/1
```

## Related
[VLANs](../02%20-%20Network%20Access/02%20-%20VLANs.md) · [ACLs](04%20-%20ACLs.md) · [SSH and Device Management](02%20-%20SSH%20and%20Device%20Management.md)

---

## Practise this topic

- [Lab - Switch Port Security](07%20-%20Lab%20-%20Switch%20Port%20Security.md)
- [Lab - DHCP Snooping and DAI](08%20-%20Lab%20-%20DHCP%20Snooping%20and%20DAI.md)

## AAA recap

- **Authentication:** who are you?
- **Authorization:** what are you allowed to do?
- **Accounting:** what did you do?

RADIUS is commonly used for network access/802.1X; TACACS+ is commonly used for administrator access to network devices. Both centralize identity decisions; choose according to the design.

---
[← Previous: 05 - Lab - Extended ACL Practice](05%20-%20Lab%20-%20Extended%20ACL%20Practice.md) · [Next: 07 - Lab - Switch Port Security →](07%20-%20Lab%20-%20Switch%20Port%20Security.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
