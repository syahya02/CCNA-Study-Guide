# Network Automation Basics

> **Core CCNA theory:** an introduction to automation principles and terms.

## Why automate?
Reduce repetitive configuration, improve consistency, collect inventory/state, detect drift and accelerate troubleshooting.

## Core building blocks
- **Controller-based networks**: a central controller manages policy/state; devices still forward traffic in the data plane.
- **Northbound APIs**: consumers/tools communicate with controllers; **southbound**: controllers communicate with devices.
- **REST APIs**: use HTTP methods — GET (read), POST (create/action), PUT/PATCH (update), DELETE (remove).
- **JSON**: structured key/value data exchanged by automation tools.
- **Ansible**: agentless network automation using playbooks; **Terraform**: declarative infrastructure provisioning.
- **AI/ML**: anomaly detection, prediction, operational assistance; validate generated configurations.

## JSON example
```json
{
  "hostname": "R1",
  "interfaces": [{"name": "GigabitEthernet0/0", "enabled": true}]
}
```

## Security
Use authenticated APIs, secrets management, HTTPS, approval workflows and config backups.

## Related
[SSH and Device Management](../05%20-%20Security%20Fundamentals/02%20-%20SSH%20and%20Device%20Management.md) · [Cisco IOS Command Reference](../07%20-%20Cisco%20IOS%20Command%20Reference/01%20-%20Cisco%20IOS%20Command%20Reference.md)

---
[← Chapter study path](README.md) · [Next: 02 - Controllers and SDN Architecture →](02%20-%20Controllers%20and%20SDN%20Architecture.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
