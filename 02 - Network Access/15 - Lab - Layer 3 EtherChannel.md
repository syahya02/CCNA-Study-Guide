# Lab - Layer 3 EtherChannel

> **Core CCNA extension** · **Platform:** Catalyst 3560 multilayer switches; feature availability varies in Packet Tracer.

## Objective
Combine two routed links between multilayer switches into one Layer 3 Port-channel.

## Topology and IP plan
`MLS1 Gi0/1,Gi0/2 == LACP Po1 == Gi0/1,Gi0/2 MLS2`

`MLS1 Po1: 10.10.10.1/30` · `MLS2 Po1: 10.10.10.2/30`

## MLS1
```cisco
enable
configure terminal
hostname MLS1
ip routing
interface range gigabitEthernet0/1 - 2
 no switchport
 channel-group 1 mode active
 no shutdown
exit
interface port-channel1
 no switchport
 ip address 10.10.10.1 255.255.255.252
 no shutdown
end
write memory
```

## MLS2
```cisco
enable
configure terminal
hostname MLS2
ip routing
interface range gigabitEthernet0/1 - 2
 no switchport
 channel-group 1 mode active
 no shutdown
exit
interface port-channel1
 no switchport
 ip address 10.10.10.2 255.255.255.252
 no shutdown
end
write memory
```

## Verify
```cisco
show etherchannel summary
show ip interface brief
show ip route connected
ping 10.10.10.2
```
From MLS1, disable one Port-channel member, check Po1 stays up, then re-enable it.

## Troubleshooting
If `no switchport` or routed Port-channels are not implemented in the selected Packet Tracer model, use a supported multilayer switch or treat this as a conceptual lab. All members must have matching settings.

## Lesson learned
A **routed EtherChannel** has its IPv4 address on the logical Port-channel, not on individual members.

---
[← Previous: 14 - Lab - EtherChannel with LACP](14%20-%20Lab%20-%20EtherChannel%20with%20LACP.md) · [Next: 16 - Lab - STP Edge Port Protection →](16%20-%20Lab%20-%20STP%20Edge%20Port%20Protection.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
