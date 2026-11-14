# FTP TFTP and File Transfer

- **FTP**: file transfer; TCP **21** control channel, separate data connection. Not encrypted by default.
- **TFTP**: simple file transfer; UDP **69** initial request, no authentication/encryption. Often used for device backups or boot workflows on trusted networks.
- **SFTP / SCP**: encrypted file transfer over SSH (typically TCP **22**), preferred for sensitive data.

## Cisco example
```cisco
copy running-config startup-config
copy running-config tftp:
show flash:
```

> Use TFTP only in isolated/trusted environments. Command availability varies with IOS image.

## Related
[SSH and Device Management](../05%20-%20Security%20Fundamentals/02%20-%20SSH%20and%20Device%20Management.md) · [Ports and IP Protocol Numbers](01%20-%20Ports%20and%20IP%20Protocol%20Numbers.md)

---
[← Previous: 11 - Lab - NTP and Syslog](11%20-%20Lab%20-%20NTP%20and%20Syslog.md) · [Next chapter: 05 - Security Fundamentals →](../05%20-%20Security%20Fundamentals/README.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
