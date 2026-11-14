# Lab - DHCP Server and Relay

> **Core CCNA lab** · **Platform:** Packet Tracer · **Status:** Guide, not simulator-verified.

## Objective
Use a DHCP server on one router to serve clients behind a different router.

## Topology / IP plan
`PC1 — R2 G0/1 (192.168.20.1/24) — R2 G0/0 (10.0.0.2/24) — R1 G0/0 (10.0.0.1/24)`

R1 is the DHCP server; R2 relays requests from PC1.

## R1 (DHCP server)
```cisco
enable
configure terminal
hostname R1
interface gigabitEthernet0/0
 ip address 10.0.0.1 255.255.255.0
 no shutdown
exit
ip route 192.168.20.0 255.255.255.0 10.0.0.2
ip dhcp excluded-address 192.168.20.1 192.168.20.9
ip dhcp pool REMOTE-LAN
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.1
 dns-server 8.8.8.8
end
write memory
```

## R2 (DHCP relay)
```cisco
enable
configure terminal
hostname R2
interface gigabitEthernet0/0
 ip address 10.0.0.2 255.255.255.0
 no shutdown
exit
interface gigabitEthernet0/1
 ip address 192.168.20.1 255.255.255.0
 ip helper-address 10.0.0.1
 no shutdown
end
write memory
```

## PC1
Set IP configuration to **DHCP**.

## Verify
```cisco
show ip dhcp binding
show ip dhcp pool
show ip interface gigabitEthernet0/1
show ip route
```
On PC1 run `ipconfig` and ping `192.168.20.1` and `10.0.0.1`.

## Troubleshooting
Check DHCP server pool, `ip helper-address` on the **client-facing interface**, route back to the client network, correct link interfaces and relay feature support.

## Lesson learned
A DHCP broadcast does not cross a router automatically; a relay forwards requests to the server.

---
[← Previous: 03 - DHCP](03%20-%20DHCP.md) · [Next: 05 - NAT and PAT →](05%20-%20NAT%20and%20PAT.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
