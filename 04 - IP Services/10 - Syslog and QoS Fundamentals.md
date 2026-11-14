# Syslog and QoS Fundamentals

## Syslog
Network devices send event messages to a collector. A syslog message has **facility** (source category) and **severity** (0–7).

| Level | Name | Interpretation |
|---:|---|---|
| 0 | Emergencies | System unusable |
| 1 | Alerts | Immediate action |
| 2 | Critical | Critical condition |
| 3 | Errors | Error |
| 4 | Warnings | Warning |
| 5 | Notifications | Normal but significant |
| 6 | Informational | Informational |
| 7 | Debugging | Debug detail |

```cisco
logging 192.168.10.10
logging trap warnings
show logging
```

## QoS (Quality of Service)
- **Classification:** identify application/traffic class.
- **Marking:** label frames/packets (for example DSCP) for downstream treatment.
- **Queuing:** decide the order in which packets leave a congested interface.
- **Congestion avoidance:** act before buffers are full.
- **Policing:** enforce a rate by dropping/remarking excess traffic.
- **Shaping:** buffer and pace packets to a configured rate.

QoS prioritises important traffic under congestion; it does not magically create bandwidth.

## Practise this topic

- [Lab - NTP and Syslog](11%20-%20Lab%20-%20NTP%20and%20Syslog.md)

---
[← Previous: 09 - NTP and SNMP Syslog](09%20-%20NTP%20and%20SNMP%20Syslog.md) · [Next: 11 - Lab - NTP and Syslog →](11%20-%20Lab%20-%20NTP%20and%20Syslog.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
