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

## Elise Rust core (VLESS and VMess)

Elise runs as a separate Rust service. Install its published amd64 or arm64 release and add nodes with:

```bash
V2bX elise install
V2bX elise add vless 123
V2bX elise add vmess 456
V2bX elise list
V2bX elise status vless-123
```

Remove an Elise node from the Go service's `Nodes` configuration before adding it here. Elise configuration is stored under `/etc/v2bx-elise`. For TLS, supply certificate and key files and configure your renewal tool to run `V2bX elise restart <instance>`. REALITY keys must be present in the panel. The fork needs a published Elise release for the install command to work. Elise uses the [PolyForm Noncommercial 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0) license.

## V2bX v0.5.0 compatibility

Before upgrading a custom or panel-managed Xray node, remove legacy transport
header types named SRTP, TLS, UTP, WeChat, and WireGuard. This does not remove
normal TLS support. Plaintext Shadowsocks methods (`none` and `plain`) and
`DisableIVCheck: true` are no longer supported.
