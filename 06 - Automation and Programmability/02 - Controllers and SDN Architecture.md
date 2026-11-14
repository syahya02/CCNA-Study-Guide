# Controllers and SDN Architecture

Traditional routers and switches each make their own local control decisions. **Controller-based networking** provides centralised policy, orchestration and visibility while switches and routers still forward packets.

- **Control plane:** builds forwarding decisions (routing and protocols).
- **Data plane:** forwards actual packets.
- **Management plane:** administrators, monitoring and configuration.
- **Underlay:** physical/IP connectivity beneath the network.
- **Overlay:** logical virtual network built above the underlay.
- **Fabric:** integrated forwarding and policy environment using underlay and overlay.
- **Northbound APIs:** applications ↔ controller.
- **Southbound APIs:** controller ↔ network devices.

Automation can deliver consistent configuration and reduce manual errors, but requires approvals, version control, validation and rollback plans.

---
[← Previous: 01 - Network Automation Basics](01%20-%20Network%20Automation%20Basics.md) · [Next: 03 - REST APIs and JSON →](03%20-%20REST%20APIs%20and%20JSON.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
