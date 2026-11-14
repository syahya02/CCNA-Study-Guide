# Lab - Site-to-Site IPsec VPN

> **Supplementary lab** · **Platform:** Cisco Packet Tracer (unless otherwise noted) · **Validation:** configurations are learning examples; test on the selected simulator/device.

## Objective
Configure a legacy IKEv1 policy-based VPN to protect traffic between two LANs, where the simulator supports the commands.

## Topology

```text
PC1 192.168.1.10 -- R1 -- 10.0.0.0/30 -- R2 -- PC2 192.168.2.10
```

## Addressing / prerequisites
R1 LAN `192.168.1.1/24`, WAN `10.0.0.1/30`; R2 WAN `10.0.0.2/30`, LAN `192.168.2.1/24`. PCs use `.1` as their gateway. **ISR4321 interface naming in this cleaned lab:** LAN G0/0/0, WAN G0/0/1; adjust for selected router model.

## Configuration

### R1

```cisco
enable
configure terminal
hostname R1
interface g0/0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
interface g0/0/1
 ip address 10.0.0.1 255.255.255.252
 no shutdown
exit
ip route 192.168.2.0 255.255.255.0 10.0.0.2
crypto isakmp policy 10
 encryption aes 256
 hash sha
 authentication pre-share
 group 14
 lifetime 86400
exit
crypto isakmp key LAB-ONLY-CHANGE-ME address 10.0.0.2
crypto ipsec transform-set VPN-SET esp-aes 256 esp-sha-hmac
exit
access-list 110 permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255
crypto map VPN-MAP 10 ipsec-isakmp
 set peer 10.0.0.2
 set transform-set VPN-SET
 match address 110
exit
interface g0/0/1
 crypto map VPN-MAP
end
wr
```

### R2

```cisco
enable
configure terminal
hostname R2
interface g0/0/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown
interface g0/0/1
 ip address 10.0.0.2 255.255.255.252
 no shutdown
exit
ip route 192.168.1.0 255.255.255.0 10.0.0.1
crypto isakmp policy 10
 encryption aes 256
 hash sha
 authentication pre-share
 group 14
 lifetime 86400
exit
crypto isakmp key LAB-ONLY-CHANGE-ME address 10.0.0.1
crypto ipsec transform-set VPN-SET esp-aes 256 esp-sha-hmac
exit
access-list 110 permit ip 192.168.2.0 0.0.0.255 192.168.1.0 0.0.0.255
crypto map VPN-MAP 10 ipsec-isakmp
 set peer 10.0.0.1
 set transform-set VPN-SET
 match address 110
exit
interface g0/0/1
 crypto map VPN-MAP
end
wr
```

## Verify

```cisco
ping 10.0.0.2
show crypto isakmp sa
show crypto ipsec sa
show crypto map
show access-lists
show ip route
```

## Troubleshooting and expected result
First confirm WAN routing. From PC1 ping `192.168.2.10` (interesting traffic), then inspect VPN state/counters. IPsec encaps/decaps should increase if VPN works; **a successful ping alone does not prove it was encrypted**.

## Notes and corrections
**Lab-only / conditional:** This reproduces the training's older IKEv1 method, not a modern deployment recommendation. Actual Packet Tracer crypto support varies. `group 14` and AES-256 may be rejected by the simulated image; do not silently substitute insecure group 1. Do not use this placeholder PSK on a real VPN. A previous R2 issue was applying crypto map to `g0/1` instead of actual ISR4321 WAN `g0/0/1`.

## Related notes
[Site-to-Site IPsec VPN](11%20-%20Site-to-Site%20IPsec%20VPN.md) · [ACLs](04%20-%20ACLs.md) · [Static and Default Routing](../03%20-%20IP%20Connectivity/04%20-%20Static%20and%20Default%20Routing.md)

---
[← Previous: 11 - Site-to-Site IPsec VPN](11%20-%20Site-to-Site%20IPsec%20VPN.md) · [Next chapter: 06 - Automation and Programmability →](../06%20-%20Automation%20and%20Programmability/README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
