# TCP-IP Model and Encapsulation

The practical TCP/IP model is commonly shown as **Application → Transport → Internet → Network Access**. This roughly combines OSI Layers 5–7 into Application and Layers 1–2 into Network Access.

## Sending an HTTP request

1. A browser prepares application data.
2. TCP adds source/destination ports and sequencing information.
3. IP adds source/destination IP addresses and determines the next hop.
4. Ethernet adds source/destination MAC addresses for the **current link**.
5. The interface sends the bits over a cable or wireless medium.

At a router, the **IP packet** is forwarded toward the destination, while the Layer 2 frame is rebuilt for the next hop.

## Address types
- **IP address** identifies a logical interface/network location.
- **MAC address** identifies a local Layer 2 interface.
- **Port number** identifies an application endpoint at Layer 4.

## Related
[OSI Model](05%20-%20OSI%20Model.md) · [Ethernet and Cabling](08%20-%20Ethernet%20and%20Cabling.md) · [TCP and UDP](10%20-%20TCP%20and%20UDP.md) · [Ports and IP Protocol Numbers](../04%20-%20IP%20Services/01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md)

---
[← Previous: 05 - OSI Model](05%20-%20OSI%20Model.md) · [Next: 07 - Unicast Broadcast and Multicast →](07%20-%20Unicast%20Broadcast%20and%20Multicast.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
