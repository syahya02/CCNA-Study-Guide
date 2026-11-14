# Virtualization Containers and VRFs

| Term | Meaning | Networking implication |
|---|---|---|
| Virtual machine (VM) | Guest OS sharing host resources through a hypervisor | Uses virtual NICs and virtual switches |
| Container | Isolated application runtime sharing the host OS kernel | Has virtual networks/namespaces and bridges |
| VRF | Virtual Routing and Forwarding: separate routing tables on one device | Allows overlapping IP ranges in isolated routing domains |

A VM usually carries its own kernel; containers generally share the host kernel. A VRF separates **Layer 3 routing**, while a VLAN separates **Layer 2 traffic**. They are not interchangeable.

## Example VRF concept
```cisco
ip vrf CUSTOMER_A
 rd 65000:10
```

*Syntax/support varies by IOS platform; this is a concept example, not a Packet Tracer exercise.*

---
[← Previous: 18 - Wireless Principles](18%20-%20Wireless%20Principles.md) · [Next: 20 - Client IP Verification →](20%20-%20Client%20IP%20Verification.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
