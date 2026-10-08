# oocap: Sovereign LINUX CAPABILITIES

<div align="center">

```
================================================================================
                                oocap
               Sovereign openOODA LINUX CAPABILITIES
================================================================================
```

**Sovereign LINUX CAPABILITIES**  
*Inspects, drops, and verifies Linux thread capability bounding sets (CAP_NET_BIND).*  
*Two Faces, One Engine:* Modern terminal ergonomics for humans • Zero-leakage MCP for AI agents  
Written in 100% pure [openOODA](https://github.com/openOODA).

[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![openOODA](https://img.shields.io/badge/openOODA-1.0-emerald.svg)](https://openooda.org)
[![Architecture: x86_64 | aarch64](https://img.shields.io/badge/Arch-x86__64%20%7C%20aarch64-lightgrey.svg)]()

</div>

---

## 1. Quick Install

### Automated Installer (Linux x86_64 & aarch64)
```bash
curl -fsSL https://openooda-tools.github.io/oocap/install.sh | bash
```

### Native Package Managers
```bash
# Arch Linux (AUR / PKGBUILD)
yay -S oocap-bin
# Or manual PKGBUILD:
cd packaging/arch && makepkg -si

# Debian / Ubuntu (.deb)
curl -fsSL https://openooda-tools.github.io/oocap/install.sh | bash -s -- --deb

# Fedora / RHEL (.rpm)
curl -fsSL https://openooda-tools.github.io/oocap/install.sh | bash -s -- --rpm
```

### Uninstallation
```bash
oocap-uninstall
# or: curl -fsSL https://openooda-tools.github.io/oocap/uninstall.sh | bash
```

---

## 2. CLI Usage

```
usage: oocap [options] [PID_OR_MASK]

Inspects, drops, and verifies Linux thread capability bounding sets.

Options:
  -p, --pid <PID>         inspect capabilities of process PID [default: self]
  -i, --inspect           inspect all capability sets for target process
  -a, --audit             audit process capabilities against negative-trust policy
      --decode <HEX>      decode 64-bit hexadecimal mask to capability names
      --encode <CAPS>     encode comma-separated capability names to hex mask
      --drop <CAPS>       calculate bounding set mask after dropping capabilities
      --systemd           generate systemd [Service] capability drop-in snippet
      --ambient           include AmbientCapabilities in systemd drop-in
      --json              output formatted as structured JSON
      --mcp               run as Model Context Protocol stdio server
  -h, --help              display this help and exit
  -v, --version           output version information and exit
```

---

## 3. Theming Integration (`oote`)

`oocap` synchronizes visual styles and status colors with [oote](https://github.com/openOODA-tools/oote):
* **Configuration:** Reads active palette from `~/.openooda/theme.oot`.
* **Environment Overrides:** Respects `$OODA_THEME` and `$NO_COLOR`.

---

## 4. Model Context Protocol (MCP)

When invoked with `--mcp`, `oocap` runs a JSON-RPC 2.0 stdio server providing structured tools for AI coding agents:

* `cap_inspect`: Inspect process capability sets (`CapInh`, `CapPrm`, `CapEff`, `CapBnd`, `CapAmb`) from `/proc/[pid]/status`.
* `cap_decode`: Decode 64-bit hexadecimal bitmask into Linux capability names.
* `cap_encode`: Encode capability names into canonical 16-hex-digit bitmask.
* `cap_audit`: Audit capability sets against privilege escalation and container escape risks.
* `cap_systemd`: Generate declarative systemd capability drop-in service configuration.

```bash
oocap --mcp
```

---

## 5. Security & Zero Ambient Authority

* **Pure Capability Bounded:** Operates strictly with explicit tokens (&SecCap, &AgentCap, &McpCap). Physical absence of ambient disk/net leakage.
* **Negative-Trust Architecture:** Strict input validation and operational limits.
* **Hermetic Binary:** Standalone zero-dependency executable.

---

## 6. License

Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
