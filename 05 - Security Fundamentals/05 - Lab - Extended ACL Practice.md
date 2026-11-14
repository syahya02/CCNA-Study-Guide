# Lab - Extended ACL Practice

> **Core CCNA lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Apply an extended ACL controlling HTTP and HTTPS access to a destination network.

## Topology

```text
PC LAN 192.168.10.0/24 -- R1 -- Server LAN 192.168.20.0/24
```

## Addressing / prerequisites
Assume R1 already routes between the two LANs. This is a supplementary practice exercise. Confirm interface directions for the chosen topology.

## Configuration

### R1 — example policy

```cisco
conf t
ip access-list extended WEB-ONLY
 permit tcp 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255 eq 80
 permit tcp 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255 eq 443
 deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255 log
 permit ip any any
interface g0/0
 ip access-group WEB-ONLY in
end
show access-lists
```

## Verify

```cisco
show access-lists
show ip interface g0/0
```

## Troubleshooting and expected result
Confirm the ACL is applied **inbound** on the intended LAN-facing interface, rule order is correct, and permitted HTTPS traffic passes while disallowed LAN-to-server protocols fail. `permit ip any any` makes the policy allow other traffic outside that restricted pair.

## Notes and corrections
Use this as an additional access-control exercise after the ACL theory.

## Related notes
[ACLs](04%20-%20ACLs.md) · [Ports and IP Protocol Numbers](../04%20-%20IP%20Services/01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md)

---
[← Previous: 04 - ACLs](04%20-%20ACLs.md) · [Next: 06 - Layer 2 Security and AAA →](06%20-%20Layer%202%20Security%20and%20AAA.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
