# EtherChannel and LACP

## Why use it
An EtherChannel bundles multiple similar physical interfaces into **one logical Port-channel**. It provides redundancy and aggregate bandwidth; STP views a correct Layer 2 bundle as one link.

- **LACP active:** negotiates; active/active and active/passive can form.
- **LACP passive:** waits; passive/passive does not negotiate.
- **Layer 2 bundle:** `switchport` and trunk/access configuration.
- **Layer 3 bundle:** `no switchport` plus IP address on the **Port-channel**.

```cisco
interface range fastEthernet0/1 - 2
 channel-group 1 mode active
exit
interface port-channel 1
 switchport mode trunk
end
show etherchannel summary
```

Member interfaces must agree on speed/duplex, trunk/access mode and VLAN settings. Load-balancing uses a hash; a single conversation may stay on one member link.

## Practise this topic

- [Lab - EtherChannel with LACP](14%20-%20Lab%20-%20EtherChannel%20with%20LACP.md)
- [Lab - Layer 3 EtherChannel](15%20-%20Lab%20-%20Layer%203%20EtherChannel.md)
- [Lab - STP Edge Port Protection](16%20-%20Lab%20-%20STP%20Edge%20Port%20Protection.md)

---
[← Previous: 12 - Lab - STP Redundant Links](12%20-%20Lab%20-%20STP%20Redundant%20Links.md) · [Next: 14 - Lab - EtherChannel with LACP →](14%20-%20Lab%20-%20EtherChannel%20with%20LACP.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
