# VAULTIX 🔐  
**Security by design, not by add-on.**

> ⚠️ **Status: Under Active Development (Alpha not yet released)**

Vaultix is an experimental Linux distribution focused on **true application isolation by default**.  
Instead of bolting on security, Vaultix builds it directly into the system architecture.

---

## 🚀 What is Vaultix?

Vaultix is a Debian-based OS that isolates every application into its own secure domain using:

- Rootless Podman containers  
- Wayland-native graphical isolation  
- AppArmor mandatory access control (MAC)  
- Strict namespace separation  

Each app runs as its own **contained environment** — not just a process.

---

## 🧠 The Core Idea

> You should always know the trust level of what you're running.

Vaultix uses a simple, color-coded mental model:

### 🟢 Green — Trusted Domain
- Full system access  
- Persistent data  
- Full network access  
- Clipboard enabled  

**Use for:**
- SSH  
- Password managers  
- Admin tools  

---

### 🟠 Amber — Normal Domain
- Limited home directory  
- Network access allowed  
- Controlled data sharing between domains  

**Use for:**
- Browsing  
- Email  
- Development  

---

### 🔴 Red — Isolated Domain
- No persistent storage  
- No host filesystem access  
- No clipboard access  
- Traffic routed via Tor  
- Container destroyed on exit  

**Use for:**
- Unknown files  
- Suspicious links  
- Malware analysis  

---

## 🏗 Architecture Overview

Vaultix is built as a **layered isolation system**:

```
[ Vaultix Host (Debian) ]
  ├─ Linux Kernel
  ├─ AppArmor (MAC)
  ├─ Wayland Compositor
  ├─ Rootless Podman
  ├─ LUKS Encryption
  └─ netavark networking

        ↓ namespace isolation

[ Domain Layer (Green / Amber / Red) ]

        ↓ per-container runtime

[ Applications ]
  ├─ 1 app = 1 container
  ├─ 1 container = 1 Wayland surface
  ├─ 1 container = 1 AppArmor profile
  └─ 1 container = 1 network namespace
```

---

## 🔑 Key Features

- 🔒 **Full-Disk Encryption (LUKS)** *(planned as default)*  
- 📦 **Container-per-App Model**  
- 🖥 **Pure Wayland (no X11 fallback)**  
- 🛡 **AppArmor per container**  
- 🧅 **Tor-only networking (Red domain)**  
- ♻️ **Ephemeral containers for high-risk tasks**  

---

## 🧪 Current Development Status

```
Kernel: Hardened Debian 12          ✅ Ready
Podman Wrapper: v0.4.x-dev         🚧 In progress
Domain Logic: Core implemented     ⚙️ Active
Wayland Isolation:                 ✅ Tested
AppArmor Enforcement:              ✅ Tested
```

---

## 🗺 Roadmap

### Phase 1 — Core Architecture (Current)
- Vaultix wrapper logic  
- Rootless Podman integration  
- Debian base hardening  

### Phase 2 — Domain Hardening
- AppArmor profiles  
- Network isolation per domain  

### Phase 3 — ISO Build System
- Reproducible builds  
- Installable image  

### Phase 4 — Public Alpha
- First testable release  
- Community feedback  

---

## 🔮 Post-Alpha Vision

- Verified boot chain (Secure Boot + dm-verity)  
- Immutable root filesystem  
- Hardware key integration (FIDO2 / YubiKey)  
- Container image attestation  

---

## 🤝 Contributing

We *definitely* need help 😄

Areas where contributions are welcome:

- Shell scripting  
- AppArmor profiles  
- Container orchestration logic  
- Documentation  

👉 See `CONTRIBUTING.md`

---

## 📦 Project Status

- ❌ Not released  
- ❌ Not installable yet  
- ✅ Actively being built  

If you’re here early—you’re part of the origin story.

---

## ⭐ Support the Project

If this idea resonates with you:

👉 **Star the repo**: https://github.com/V1king0/vaultix  
👉 Follow development  
👉 Open issues / suggest ideas  

---

## 📜 License

Dual licensed:

- MIT  
- GPLv3  

---

## 🧊 Philosophy

> **Compromise should be contained—not catastrophic.**

---

## 🛠 Built With

- Debian  
- Podman  
- Wayland  
- AppArmor  

---

```
$ vaultix --status
↳ Building something dangerous (for attackers)
↳ Building something safe (for you)
```
