# Cisco IOS Command Reference

| Command | Why use it |
|---|---|
| `enable` | Enter privileged EXEC mode (`#`) |
| `configure terminal` | Enter global config mode (`(config)#`) |
| `hostname R1` | Set device name |
| `interface g0/0` | Select interface; name depends on model |
| `no shutdown` | Administratively enable interface |
| `exit` | Return one config level |
| `end` | Return to privileged EXEC mode |
| `write memory` | Save running config to startup config (`wr` shorthand) |
| `copy running-config startup-config` | Explicit save command |
| `show running-config` | Inspect active configuration |
| `show startup-config` | Inspect saved configuration |
| `?` | Context-sensitive help |
| `do show ip route` | Run show command from configuration mode (supported IOS) |

## Config modes
```text
Router>          user EXEC
Router#          privileged EXEC
Router(config)#  global configuration
Router(config-if)# interface configuration
Router(config-router)# routing protocol configuration
```

## Related
[Interface and IPv4 Commands](02%20-%20Interface%20and%20IPv4%20Commands.md) · [Switching Commands](03%20-%20Switching%20Commands.md) · [Routing Commands](04%20-%20Routing%20Commands.md) · [Verification and Troubleshooting Commands](06%20-%20Verification%20and%20Troubleshooting%20Commands.md)

---

[← Main study guide](../README.md)

---
[← Chapter study path](README.md) · [Next: 02 - Interface and IPv4 Commands →](02%20-%20Interface%20and%20IPv4%20Commands.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
