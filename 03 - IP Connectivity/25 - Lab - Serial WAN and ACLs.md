# Lab - Serial WAN and ACLs

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Practise a two-router serial link, serial encapsulation, and a standard ACL.

## Topology

```text
R1 Serial2/0 ===== Serial2/0 R2
```

## Addressing / prerequisites
Use a Packet Tracer router with serial modules installed. Link `1.1.1.1/8` ↔ `1.1.1.2/8`. `clock rate` belongs to the **DCE** end only. Legacy lab uses HDLC and standard numbered ACLs. Interface names vary by model.

## Configuration

### R1 (DCE only if Packet Tracer identifies this end as DCE)

```cisco
conf t
interface serial 2/0
 ip address 1.1.1.1 255.0.0.0
 encapsulation hdlc
 bandwidth 64
 clock rate 64000
 description TO-R2
 no shutdown
exit
access-list 1 deny host 150.150.150.1
access-list 1 permit any
interface serial 2/0
 ip access-group 1 in
end
wr
```

### R2

```cisco
conf t
interface serial 2/0
 ip address 1.1.1.2 255.0.0.0
 encapsulation hdlc
 bandwidth 64
 description TO-R1
 no shutdown
exit
access-list 1 deny host 50.50.50.1
access-list 1 permit any
interface serial 2/0
 ip access-group 1 in
end
wr
```

## Verify

```cisco
show controllers serial 2/0
show interfaces serial 2/0
show ip interface brief
show access-lists
show ip interface serial 2/0
```

## Troubleshooting and expected result
Link comes up with matching Layer 2 encapsulation and correct clocking. Note these ACLs only have an effect if matching source traffic actually crosses the interface; optional loopback hosts/routes must be configured. Telnet/password examples from the old source were intentionally not reused.

## Notes and corrections
Do not apply `clock rate` at both ends unless the simulator explicitly treats each as DCE in a different topology. Use `show controllers serial` to identify DCE.

## Related notes
[ACLs](../05%20-%20Security%20Fundamentals/04%20-%20ACLs.md) · [SSH and Device Management](../05%20-%20Security%20Fundamentals/02%20-%20SSH%20and%20Device%20Management.md) · [Static and Default Routing](04%20-%20Static%20and%20Default%20Routing.md)

---
[← Previous: 24 - Serial WAN Basics](24%20-%20Serial%20WAN%20Basics.md) · [Next chapter: 04 - IP Services →](../04%20-%20IP%20Services/README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
