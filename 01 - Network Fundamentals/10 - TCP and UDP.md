# TCP and UDP

Both protocols operate at **Transport (OSI Layer 4)** and use source/destination **port numbers**.

| TCP | UDP |
|---|---|
| Connection-oriented; handshake | Connectionless |
| Reliable, ordered byte stream | Datagram delivery; no built-in delivery/order guarantee |
| Sequence numbers, acknowledgements, retransmissions | Lightweight 8-byte header |
| Flow control with a receive window | No native flow control |
| Typical use: SSH, HTTPS | Typical use: DNS, DHCP, NTP, streaming protocols |

## TCP three-way handshake
`SYN → SYN-ACK → ACK` establishes a connection. The sender tracks sequence and acknowledgement numbers.

## TCP windowing
The receive window indicates how many **bytes** the sender may send without exceeding the receiver's advertised buffer capacity. Window scaling and congestion control affect real throughput.

## Headers
- **TCP**: source port, destination port, sequence number, acknowledgment number, flags, window, checksum, options, payload.
- **UDP**: source port (16 bits), destination port (16), length (16), checksum (16), payload. **Fixed header = 8 bytes**.

> Do not confuse TCP/UDP **port numbers** with the **IP protocol number** used to identify TCP (6) or UDP (17).

## Related
[OSI Model](05%20-%20OSI%20Model.md) · [Ports and IP Protocol Numbers](../04%20-%20IP%20Services/01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md) · [DNS](../04%20-%20IP%20Services/02%20-%20DNS.md) · [DHCP](../04%20-%20IP%20Services/03%20-%20DHCP.md)

---
[← Previous: 09 - Interface and Cable Troubleshooting](09%20-%20Interface%20and%20Cable%20Troubleshooting.md) · [Next: 11 - IPv4 Addressing →](11%20-%20IPv4%20Addressing.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
