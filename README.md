# CCNA — Networking Study Guide & Practical Labs

A beginner-friendly, **theory → hands-on lab → verification** learning path covering Cisco networking fundamentals, switching, routing, IP services, security and automation.

## Why I made this guide

I organised these notes while studying networking and practising Cisco IOS configurations. My training was particularly lab-focused, so I wanted a guide that explains *why* a technology works before asking someone to configure it. I also expanded areas that benefit from more theory or a short exercise.

This is a learning and revision resource—not an official Cisco course, a collection of exam dumps, or a promise that every simulator command works on every IOS image.

## How to study

1. **Start with a chapter README:** it sets out the reading order.
2. **Read the theory:** understand the purpose, addressing and terms first.
3. **Do the immediately following practical lab:** build the topology, type the commands and verify the result.
4. **Break and fix it:** change one setting, observe the failure and diagnose it.
5. **Move to the next topic:** the path continues inside the same chapter. Use the [command reference](07%20-%20Cisco%20IOS%20Command%20Reference/README.md) and [revision questions](08%20-%20Revision%20and%20Practice%20Questions/README.md) as needed.

**File naming:** Files use one numbered sequence within each chapter. Theory and practicals follow the same order; lab filenames simply use `Lab -` after the sequence number (for example, `03 - IP Connectivity/05 - Lab - Static Routes and Loopbacks.md`). Follow the **Next lesson** link at the end of each note to continue.

**How to read the labels:** **Core CCNA** means material aligned with the CCNA v1.1 objectives. **Supplementary** means extra networking knowledge or a deeper practical than those objectives require; it stays in the relevant chapter, not in a separate folder.

## Start the learning path

| Step | Chapter | Main focus | Weight (v1.1) |
|---:|---|---|---:|
| 1 | [Network Fundamentals](01%20-%20Network%20Fundamentals/README.md) | OSI/TCP-IP, IPv4/IPv6, subnetting, cabling, wireless basics | 20% |
| 2 | [Network Access](02%20-%20Network%20Access/README.md) | Switching, VLANs, trunking, STP, EtherChannel, WLC | 20% |
| 3 | [IP Connectivity](03%20-%20IP%20Connectivity/README.md) | Route selection, static routes, OSPF, gateway redundancy | 25% |
| 4 | [IP Services](04%20-%20IP%20Services/README.md) | DHCP, DNS, NAT, NTP, SNMP, Syslog, QoS | 10% |
| 5 | [Security Fundamentals](05%20-%20Security%20Fundamentals/README.md) | Secure access, ACLs, Layer 2 security, wireless security | 15% |
| 6 | [Automation and Programmability](06%20-%20Automation%20and%20Programmability/README.md) | SDN, APIs, JSON, automation, AI/ML | 10% |

### Example: a natural theory-to-lab sequence

For VLANs I recommend: **VLAN concepts → trunks and 802.1Q → VLAN/trunk lab → router-on-a-stick theory → inter-VLAN routing lab**. For OSPF: **OSPF concepts → Router ID/DR/BDR → single-area OSPF lab → DR/BDR observation lab**.

The chapter READMEs contain the exact links so I don't need to maintain a duplicate lab catalogue here.

## Repository layout

```text
CCNA-Study-Guide/
├── README.md
├── 01 - Network Fundamentals/
│   ├── README.md
│   ├── 01 - Network Foundations.md
│   └── ... theory and nearby practical labs
├── 02 - Network Access/
├── 03 - IP Connectivity/
├── 04 - IP Services/
├── 05 - Security Fundamentals/
├── 06 - Automation and Programmability/
├── 07 - Cisco IOS Command Reference/
└── 08 - Revision and Practice Questions/
```

Every chapter includes a short ordered index. The folder contains only publishable Markdown files: **no training screenshots or raw documents**.

## Practical lab format

The labs use a consistent flow: **objective → topology and addressing → per-device configuration → verification → expected behaviour → troubleshooting → key lesson**. I use Cisco Packet Tracer for most exercises, although features and interface names vary with hardware and simulator version. Some supplementary or automation labs require a different tool or are interpretive exercises rather than Packet Tracer simulations.

Commands and expected output are not a substitute for testing: I distinguish expected results from independently verified ones. Use documentation-only example IP ranges in public learning environments where possible, and adapt older training addresses for isolated labs.

## What is included beyond the exam?

I retained [RIPv2](03%20-%20IP%20Connectivity/README.md), [EIGRP](03%20-%20IP%20Connectivity/README.md), [multi-area OSPF](03%20-%20IP%20Connectivity/README.md), [VTP](02%20-%20Network%20Access/README.md) and the detailed [IPsec site-to-site lab](05%20-%20Security%20Fundamentals/README.md) as **Supplementary** topics. They are useful for understanding wider networking, even where the current exam tests only general concepts or uses different protocols.

## Verification and notes

- Official objective reference: [Cisco CCNA 200-301 exam topics](https://learningnetwork.cisco.com/s/ccna-exam-topics).
- **Exam version:** this guide maps to **CCNA v1.1** (current as of November 2026). Cisco has announced **v2.0 from February 3, 2027**; consult the official objectives when studying for an exam after that date.
- Use unique secrets and approved addressing in real networks. Any sample credentials are for isolated labs only.
- If a Packet Tracer image rejects an advanced command, confirm platform support before assuming the syntax is wrong.

## Final note

I find networking easier to learn by following one cycle: **understand → configure → verify → troubleshoot**. This repository follows that same sequence so each topic can be studied independently or as part of the complete path.

---
[Start studying: 01 - Network Foundations →](01%20-%20Network%20Fundamentals/01%20-%20Network%20Foundations.md)
