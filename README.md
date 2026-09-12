# V2bX installation script

This repository contains the installation and management scripts for
[phungvanquy/v2bx-new](https://github.com/phungvanquy/v2bx-new), a multi-core
V2Board node server supporting V2Ray, Trojan, Shadowsocks, and Hysteria.

## Documentation

[V2bX usage guide](https://v2bx.v-50.me/)

## One-click installation

```bash
wget -N https://raw.githubusercontent.com/phungvanquy/v2bx-script-new/refs/heads/main/install.sh && bash install.sh
```

The installer downloads the latest V2bX release for amd64, arm64, or s390x,
verifies its published SHA-256 digest, and stages it before replacing an existing
installation. If an upgraded service cannot start, the previous installation is
restored automatically.

## V2bX v0.5.0 compatibility

Before upgrading a custom or panel-managed Xray node, remove legacy transport
header types named SRTP, TLS, UTP, WeChat, and WireGuard. This does not remove
normal TLS support. Plaintext Shadowsocks methods (`none` and `plain`) and
`DisableIVCheck: true` are no longer supported.
