# Client IP Verification

Check the local host **before troubleshooting the upstream network**.

| Platform | Address and gateway | Connectivity tests |
|---|---|---|
| Windows | `ipconfig /all`, `route print` | `ping`, `tracert`, `nslookup` |
| Linux | `ip address`, `ip route` | `ping`, `traceroute`, `dig` |
| macOS | `ifconfig`, `netstat -rn` | `ping`, `traceroute`, `dig` |

Recommended order: localhost → own address → default gateway → remote IP → DNS hostname. If an IP ping works but a name does not, check DNS rather than immediately changing routes.

---
[← Previous: 19 - Virtualization Containers and VRFs](19%20-%20Virtualization%20Containers%20and%20VRFs.md) · [Next chapter: 02 - Network Access →](../02%20-%20Network%20Access/README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
