# Questions - Fundamentals and IP

**1. What is the purpose of the OSI model?**
A layered conceptual model to describe and troubleshoot network communication.

**2. Which OSI layers handle IP, Ethernet and TCP?**
IP: Layer 3; Ethernet framing: Layer 2; TCP: Layer 4.

**3. What is encapsulation?**
Adding protocol headers/trailers while data moves down the network stack.

**4. Why is a switch not the same as a router?**
A Layer 2 switch forwards frames within VLANs using MACs; a router forwards IP packets between networks.

**5. What is the decimal value of `11111111`?**
255; 256 needs nine binary bits.

**6. What is the correct network for `172.16.1.1/16`?**
`172.16.0.0/16`.

**7. How many usable host addresses in a conventional `/26`?**
62.

**8. List private IPv4 ranges.**
`10/8`, `172.16/12`, `192.168/16`.

**9. What is CIDR?**
Classless prefix notation, e.g. `192.168.10.0/24`.

**10. What are key TCP vs UDP differences?**
TCP reliable ordered byte stream and connection establishment; UDP connectionless datagrams without built-in delivery guarantees.

**11. What is the UDP header length?**
8 bytes.

**12. What is TCP windowing?**
Receive-side flow control limiting unacknowledged bytes relative to the advertised window.

**13. What does IPv6 `::1` mean?**
Loopback address.

**14. What is the difference between unicast and multicast?**
One receiver versus a selected receiver group.

## Review
[OSI Model](../01%20-%20Network%20Fundamentals/05%20-%20OSI%20Model.md) · [Subnetting CIDR and VLSM](../01%20-%20Network%20Fundamentals/13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [TCP and UDP](../01%20-%20Network%20Fundamentals/10%20-%20TCP%20and%20UDP.md)

---

[← Main study guide](../README.md)

---
[← Chapter study path](README.md) · [Next: 02 - Questions - Switching and VLANs →](02%20-%20Questions%20-%20Switching%20and%20VLANs.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
