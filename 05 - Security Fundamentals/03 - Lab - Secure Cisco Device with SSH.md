# Lab - Secure Cisco Device with SSH

> **Core CCNA lab** · **Platform:** Packet Tracer (Cisco IOS router/switch) · **Status:** Guide, not simulator-verified.

## Objective
Enable encrypted CLI management and prevent Telnet access.

## Topology
`Admin PC 192.168.10.10/24 — SW1 — R1 G0/0 192.168.10.1/24`

## Router configuration
```cisco
enable
configure terminal
hostname R1
ip domain-name lab.example.test
username admin privilege 15 secret LabSSH-ChangeThis123!
crypto key generate rsa modulus 2048
ip ssh version 2
interface gigabitEthernet0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
exit
line vty 0 4
 login local
 transport input ssh
end
write memory
```

**Packet Tracer note:** Some devices prompt interactively for RSA modulus or support different `crypto key generate rsa` syntax. Use `crypto key generate rsa` and enter 2048 when prompted if needed.

## Verify
On R1:
```cisco
show ip ssh
show ssh
show ip interface brief
```
From PC1's terminal: `ssh -l admin 192.168.10.1` (where Packet Tracer supports it). Telnet should be rejected by the VTY transport policy.

## Troubleshooting
Confirm `hostname` and `ip domain-name` before RSA keys, successful IP ping, local username, matching VTY `login local` and `transport input ssh`.

## Lesson learned
SSH encrypts management sessions; Telnet does not.

---
[← Previous: 02 - SSH and Device Management](02%20-%20SSH%20and%20Device%20Management.md) · [Next: 04 - ACLs →](04%20-%20ACLs.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
