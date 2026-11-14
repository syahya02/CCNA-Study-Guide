# Binary and Subnet Quick Reference

## Place values (one octet)

```text
Bit:     7    6    5    4    3    2    1    0
Value: 128   64   32   16    8    4    2    1
```

`11000000` = 128 + 64 = **192**. Eight 1s (`11111111`) = **255**, not 256. Decimal 256 requires nine bits.

## Powers of two

| n | 2ⁿ | n | 2ⁿ |
|---:|---:|---:|---:|
| 1 | 2 | 8 | 256 |
| 2 | 4 | 9 | 512 |
| 3 | 8 | 10 | 1,024 |
| 4 | 16 | 11 | 2,048 |
| 5 | 32 | 12 | 4,096 |
| 6 | 64 | 13 | 8,192 |
| 7 | 128 | 14 | 16,384 |

## Common masks

| CIDR | Mask | Addresses | Typical usable hosts* |
|---|---|---:|---:|
| /24 | 255.255.255.0 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 8 | 6 |
| /30 | 255.255.255.252 | 4 | 2 |
| /31 | 255.255.255.254 | 2 | Both addresses on appropriate point-to-point links |
| /32 | 255.255.255.255 | 1 | Single host/route |

*For conventional IPv4 subnets: usable = 2^(32 − prefix) − 2. Exceptions include /31 and /32.

## Related
[Subnetting CIDR and VLSM](13%20-%20Subnetting%20CIDR%20and%20VLSM.md) · [IPv4 Addressing](11%20-%20IPv4%20Addressing.md)

---
[← Previous: 11 - IPv4 Addressing](11%20-%20IPv4%20Addressing.md) · [Next: 13 - Subnetting CIDR and VLSM →](13%20-%20Subnetting%20CIDR%20and%20VLSM.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
