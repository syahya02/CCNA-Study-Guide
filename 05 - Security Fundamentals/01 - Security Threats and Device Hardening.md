# Security Threats and Device Hardening

## Four core terms
- **Threat:** potential cause of harm (attacker, malware, power failure).
- **Vulnerability:** weakness (unpatched software, default password).
- **Exploit:** method or code taking advantage of a weakness.
- **Mitigation:** control reducing likelihood or impact.

## Basic controls
- Restrict physical access to network closets and console ports.
- Use unique admin accounts, strong secrets, MFA where supported, and least privilege.
- Prefer SSH and encrypted management protocols to Telnet/HTTP.
- Restrict management sources with an ACL, keep firmware maintained, secure unused ports, save and back up configurations.
- Separate user, guest and management networks.

## Cisco local login example
```cisco
conf t
username admin privilege 15 secret <STRONG-LAB-PASSWORD>
enable secret <STRONG-LAB-ENABLE-SECRET>
service password-encryption
line console 0
 login local
exit
line vty 0 4
 login local
 transport input ssh
end
```

**Note:** `service password-encryption` provides weak obscuring of certain stored passwords; it is **not a replacement** for properly protected secret hashes.

Review: password policy vs certificates vs biometrics vs MFA; user awareness and physical access controls are also part of network security.

---
[← Chapter study path](README.md) · [Next: 02 - SSH and Device Management →](02%20-%20SSH%20and%20Device%20Management.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
