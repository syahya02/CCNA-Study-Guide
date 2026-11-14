# Lab - VTP Server and Client

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Propagate a VLAN database from one Cisco multilayer switch to another across a trunk.

## Topology

```text
MLS1 (VTP server) === 802.1Q trunk === MLS2 (VTP client)
```

## Addressing / prerequisites
Both VTP domain `COMPANY`, VTP version 2; VLANs 10 HR, 20 IT, 30 FINANCE. Use matching VTP authentication settings if enabled. Interface G0/1 to G0/1 (adapt to model).

## Configuration

### MLS1 — server

```cisco
enable
conf t
hostname MLS1
vtp domain COMPANY
vtp mode server
vtp version 2
vlan 10
 name HR
vlan 20
 name IT
vlan 30
 name FINANCE
interface g0/1
 switchport mode trunk
 no shutdown
end
wr
```

### MLS2 — client

```cisco
enable
conf t
hostname MLS2
vtp domain COMPANY
vtp mode client
vtp version 2
interface g0/1
 switchport mode trunk
 no shutdown
end
wr
```

## Verify

```cisco
show vtp status
show vlan brief
show interfaces trunk
```

## Troubleshooting and expected result
MLS2 should learn the VLANs from MLS1. VTP **does not** configure gateways/SVIs or turn on `ip routing`. Always inspect VTP revision number before joining a production domain.

## Related notes
[VTP](20%20-%20VTP.md) · [VLANs](02%20-%20VLANs.md) · [Trunking and 802.1Q](03%20-%20Trunking%20and%20802.1Q.md)

---
[← Previous: 20 - VTP](20%20-%20VTP.md) · [Next chapter: 03 - IP Connectivity →](../03%20-%20IP%20Connectivity/README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
