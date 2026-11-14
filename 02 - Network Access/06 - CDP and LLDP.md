# CDP and LLDP

Both are **Layer 2 discovery protocols** that identify directly connected neighbors; they do not create IP routes.

| Protocol | Vendor | Common command |
|---|---|---|
| CDP | Cisco-proprietary | `show cdp neighbors detail` |
| LLDP | Open standard | `show lldp neighbors detail` |

```cisco
show cdp neighbors
show cdp neighbors detail
configure terminal
lldp run
end
show lldp neighbors
```

A missing neighbor can indicate a cable, switchport, protocol-enable or device-support problem. Disable discovery on sensitive/untrusted interfaces if your design requires it.

## Practise this topic

- [Lab - CDP and LLDP Discovery](07%20-%20Lab%20-%20CDP%20and%20LLDP%20Discovery.md)

---
[← Previous: 05 - Native and Voice VLANs](05%20-%20Native%20and%20Voice%20VLANs.md) · [Next: 07 - Lab - CDP and LLDP Discovery →](07%20-%20Lab%20-%20CDP%20and%20LLDP%20Discovery.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
