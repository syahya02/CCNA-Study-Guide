# NTP and SNMP Syslog

## NTP — Network Time Protocol
Synchronizes device clocks for logs, monitoring and authentication. Typically **UDP 123**.
```cisco
ntp server 192.0.2.10
show ntp associations
show clock
```

## SNMP — Simple Network Management Protocol
Lets a **network management system (NMS)** poll/monitor devices and receive event notifications.
- SNMP polling: **UDP 161**.
- Traps/informs: **UDP 162**.
- SNMPv3 supports authentication and privacy; avoid cleartext v1/v2c community strings in production.

## Syslog
Centralizes event logs with severity levels **0 (Emergency) through 7 (Debug)**. Traditional network syslog uses UDP **514**, although secure transports also exist.
```cisco
logging host 192.0.2.20
show logging
```

## Related
[Ports and IP Protocol Numbers](01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md) · [SSH and Device Management](../05%20-%20Security%20Fundamentals/02%20-%20SSH%20and%20Device%20Management.md)

---
[← Previous: 08 - Lab - Static NAT and Dynamic NAT Pool](08%20-%20Lab%20-%20Static%20NAT%20and%20Dynamic%20NAT%20Pool.md) · [Next: 10 - Syslog and QoS Fundamentals →](10%20-%20Syslog%20and%20QoS%20Fundamentals.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
