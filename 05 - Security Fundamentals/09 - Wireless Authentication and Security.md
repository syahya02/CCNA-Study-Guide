# Wireless Authentication and Security

| Protocol | Summary |
|---|---|
| WEP | Broken and obsolete; do not deploy |
| WPA | Transitional and outdated |
| WPA2-Personal | Common PSK-based Wi-Fi authentication; use AES/CCMP |
| WPA2-Enterprise | 802.1X with RADIUS-backed identity |
| WPA3-Personal | SAE password authentication; improved resistance to offline guessing |

A guest WLAN should generally be isolated from internal networks. **SSID hiding is not encryption.**

### WPA2-PSK practice checklist
Set a unique SSID, use WPA2-Personal/AES, choose a strong passphrase, connect a client, then check DHCP and connectivity. Do not use insecure WEP just to make an old simulator work.

## Practise this topic

- [Lab - WPA2 Wireless Client](10%20-%20Lab%20-%20WPA2%20Wireless%20Client.md)

---
[← Previous: 08 - Lab - DHCP Snooping and DAI](08%20-%20Lab%20-%20DHCP%20Snooping%20and%20DAI.md) · [Next: 10 - Lab - WPA2 Wireless Client →](10%20-%20Lab%20-%20WPA2%20Wireless%20Client.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
