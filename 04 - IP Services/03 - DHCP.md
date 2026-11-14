# DHCP

**Dynamic Host Configuration Protocol (DHCP)** assigns network settings to clients: IP address, subnet mask, default gateway, DNS servers, lease time and other options.

## DORA (IPv4 lease process)

1. **Discover** — client looks for DHCP servers, often broadcast.
2. **Offer** — server proposes a lease, broadcast or unicast depending on context.
3. **Request** — client selects/requests the offer.
4. **Acknowledge** — server confirms the lease.

- UDP **67** = DHCP server; UDP **68** = client.
- **DHCP relay** (`ip helper-address`) forwards client broadcasts across routed subnets to a DHCP server.
- **APIPA** `169.254.0.0/16` is an IPv4 link-local fallback, **not** an application-layer protocol.
- **BOOTP** is a related older protocol; DHCP builds on BOOTP message format.

## Cisco example
```cisco
ip dhcp excluded-address 192.168.10.1 192.168.10.20
ip dhcp pool HR
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 1.1.1.1
```

## Verify
```cisco
show ip dhcp binding
show ip dhcp pool
show running-config | section dhcp
```

## Related
[DNS](02%20-%20DNS.md) · [IPv4 Addressing](../01%20-%20Network%20Fundamentals/11%20-%20IPv4%20Addressing.md) · [Ports and IP Protocol Numbers](01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md)

---

## Practise this topic

- [Lab - DHCP Server and Relay](04%20-%20Lab%20-%20DHCP%20Server%20and%20Relay.md)

## DHCP relay

When the DHCP server is on another subnet, configure `ip helper-address <server-ip>` on the router interface receiving client broadcasts. The relay carries requests to the remote server and identifies the client network.

Follow the linked DHCP relay lab above to configure and test this on two routers.

---
[← Previous: 02 - DNS](02%20-%20DNS.md) · [Next: 04 - Lab - DHCP Server and Relay →](04%20-%20Lab%20-%20DHCP%20Server%20and%20Relay.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
