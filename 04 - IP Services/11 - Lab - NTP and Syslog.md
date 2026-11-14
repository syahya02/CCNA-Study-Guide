# Lab - NTP and Syslog

> **Core CCNA configuration practice** · **Platform:** Packet Tracer (feature support varies).

## Objective
Synchronize a router's time and point logging to a network server.

## Topology / addressing
`R1 G0/0 (10.0.0.1/24) — SW1 — R2 G0/0 (10.0.0.2/24)` and `Server-PT (10.0.0.10/24)` on the same switch. On Server-PT, enable **Syslog** in Services if available.

## R1 — time source (lab only)
```cisco
enable
configure terminal
interface gigabitEthernet0/0
 ip address 10.0.0.1 255.255.255.0
 no shutdown
exit
ntp master 3
end
```

## R2 — NTP client and syslog sender
```cisco
enable
configure terminal
interface gigabitEthernet0/0
 ip address 10.0.0.2 255.255.255.0
 no shutdown
exit
ntp server 10.0.0.1
service timestamps log datetime msec
logging 10.0.0.10
logging trap informational
end
write memory
```

## Verify
```cisco
show ntp associations
show ntp status
show logging
```

Generate a benign log event by administratively changing a spare interface state. Inspect Syslog service on Server-PT.

## Troubleshooting
NTP convergence takes time and some simulators limit NTP or remote syslog features. Ensure IP reachability first and avoid claiming sync before checking `show ntp status`.

## Lesson learned
Consistent time and central logs make troubleshooting and event correlation far more reliable.

---
[← Previous: 10 - Syslog and QoS Fundamentals](10%20-%20Syslog%20and%20QoS%20Fundamentals.md) · [Next: 12 - FTP TFTP and File Transfer →](12%20-%20FTP%20TFTP%20and%20File%20Transfer.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
