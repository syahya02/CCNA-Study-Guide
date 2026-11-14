# Routing Decisions and Longest Prefix Match

A router decides where to forward a packet using **longest prefix match (LPM)** first. Administrative Distance (AD) and metric help choose which route to install when sources compete for the **same prefix**.

Example routing table:
```text
S 10.0.0.0/8 via 192.0.2.1
O 10.10.0.0/16 via 192.0.2.2
S 10.10.10.0/24 via 192.0.2.3
```

Destination `10.10.10.55` matches all three. The router selects `/24` even if another matching route has a lower AD because `/24` is most specific.

## Decision order
1. Find the most-specific destination prefix.
2. For competing paths to the *same* prefix, prefer the lower AD across routing sources.
3. Within the selected protocol, apply the routing metric.

**Default route** `0.0.0.0/0` matches everything not covered by a more specific route. `show ip route` displays the installed paths and gateway of last resort.

---
[← Previous: 02 - Routing Table and Administrative Distance](02%20-%20Routing%20Table%20and%20Administrative%20Distance.md) · [Next: 04 - Static and Default Routing →](04%20-%20Static%20and%20Default%20Routing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
