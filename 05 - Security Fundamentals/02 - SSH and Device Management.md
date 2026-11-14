# SSH and Device Management

**SSH** encrypts remote command-line sessions (TCP **22**). **Telnet** (TCP 23) sends data in plaintext and should not be used for production remote administration. **HTTPS** protects HTTP with modern TLS.

## Basic Cisco SSH setup
```cisco
conf t
hostname SW1
ip domain-name lab.example
username admin privilege 15 secret <strong-lab-password>
crypto key generate rsa modulus 2048
ip ssh version 2
line vty 0 4
 login local
 transport input ssh
end
show ip ssh
```

Use suitable management IP connectivity, limited admin access, secure authentication and AAA where possible. `enable secret` is preferable to `enable password`.

## Important correction
In some older lab examples, a VTY password is set but `login` is omitted; line passwords alone may not activate remote authentication. Modern configurations should use `login local` and SSH rather than Telnet.

## Related
[ACLs](04%20-%20ACLs.md) · [Ports and IP Protocol Numbers](../04%20-%20IP%20Services/01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md) · [Lab - Serial WAN and ACLs](../03%20-%20IP%20Connectivity/25%20-%20Lab%20-%20Serial%20WAN%20and%20ACLs.md)

---

## Practise this topic

- [Lab - Secure Cisco Device with SSH](03%20-%20Lab%20-%20Secure%20Cisco%20Device%20with%20SSH.md)

---
[← Previous: 01 - Security Threats and Device Hardening](01%20-%20Security%20Threats%20and%20Device%20Hardening.md) · [Next: 03 - Lab - Secure Cisco Device with SSH →](03%20-%20Lab%20-%20Secure%20Cisco%20Device%20with%20SSH.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
