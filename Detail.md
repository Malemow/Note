# Personal IT Architecture

> :LiUserRoundPen: Owner: Nick  
> :LiBackpack: Scope: Home-Lab & Personal Development Environment  
> :LiTimer: Last Updated: 2025-12-23

> Security Notice:  
> This document is intended for public sharing.  
> Internal network details such as VLAN IDs, IP subnets, addressing schemes,
> firewall rules, and host mappings are deliberately omitted to avoid exposing
> sensitive infrastructure information.
---

## 1. Overview

This document describes the architecture, tooling, and operational design of my personal IT environment.  
The goals are:

- Provide a clear system overview
- Enable reproducible rebuild / disaster recovery
- Serve as long-term operations reference
- Record major design decisions and changes

**Design Principles**

- Single gateway, centralized routing & security
- Layered architecture (Network / Server / Client)
- Automation and observability first
- Documentation as code

---

## 2. Network Architecture

### 2.1 Topology

- ISP → UniFi UDM → LAN / VLANs → Servers / Clients
- Wi-Fi clients connect via TP-Link AX50 (AP mode)

### 2.2 Network Devices

#### Gateway
- Device: UniFi UDM
- Notes:
  - Single L3 gateway design
  - Centralized policy control

#### Wi-Fi Access Point
- Device: TP-Link AX50
- Mode: Bridge / AP Mode
- Roles:
  - L2 wireless access only
- Notes:
  - Routing & DHCP disabled
  - Avoid double NAT

### 2.3 Logical Segmentation (Abstract)

The internal network is logically segmented into multiple zones, such as:

- Infrastructure zone
- Server / service zone
- Client zone
- IoT / untrusted zone

Segmentation is enforced via VLANs and firewall policies on the gateway.
Exact VLAN IDs and subnet ranges are intentionally omitted in this document.

---

## 3. Server & Services

### 3.1 Virtualization & Storage

- ESXi v8.03u
	- vCenter v8.03u
- TrueNAS v25.10.0.1 (Goldeye)

> Role: Core infrastructure for VM management and storage.

### 3.2 Core Services

- Nginx — Reverse proxy
- Grafana — Observability platform
	- Loki — Log aggregation
	- Alloy — Metrics / log agent
- Line Bot — 記帳機器人
- Jump Host — SSH entry point
- Suwayomi — Comics Server
- Rsync Server - Backup (Rsysnc)
- DNS
	- DNSDist
	- PDNS Auth
	- PDNS Recursor

> Role: Internal services, monitoring, and secure access.

---

## 4. Client Environment

### 4.1 IDE / Editor

#### JetBrains Toolchain
- WebStorm — Web / Frontend
- RustRover — Rust
- CLion — C / C++
- GoLand — Golang
- PhpStorm — PHP / Laravel
- Rider — C# / .NET
- DataGrip — Database management

> Role: Primary full-feature IDE stack.

#### Neovim (Customized)

Repo: https://github.com/Malemow/neovim

Key capabilities:
- LSP & completion: `lsp.lua`, `nvim-cmp.lua`
- Navigation & search: `telescope.lua`, `grug-far.lua`, `aerial.lua`
- Git: `gitsigns.lua`, `lazygit.lua`
- UI/UX: `lualine.lua`, `noice.lua`, `bufferline.lua`, `mini-*`
- Debug: `nvim-dap.lua`
- File explorer: `nvim-tree.lua`
- AI assist: `claudecode.lua`
- Tree-sitter: `treesitter.lua`

> Role: Lightweight, keyboard-centric editor with deep customization.

---

### 4.2 Terminal Environment

#### macOS
---

| Item            | Value / Tool                                    | Note                          |
| --------------- | ----------------------------------------------- | ----------------------------- |
| Terminal        | iTerm2                                          | Primary terminal emulator     |
| Package Manager | Homebrew                                        | Package management            |
| Shell           | zsh + oh-my-zsh                                 | Interactive shell framework   |
| Theme           | Dracula Pro                                     |                               |
| Monitor         | btop / ctop                                     | System & container monitoring |
| File List       | eza                                             | Modern `ls` replacement       |
| Search          | fzf / ripgrep                                   | Fuzzy finder & grep           |
| Repo Manager    | ghq                                             | Git repository management     |
| Config Repo     | https://github.com/Malemow/system-home/tree/mac | macOS shell config            |

#### Windows
---

| Item            | Value / Tool                                        | Note                      |
| --------------- | --------------------------------------------------- | ------------------------- |
| Terminal        | Windows Terminal                                    | Primary terminal emulator |
| Shell           | PowerShell                                          | Default Windows shell     |
| Theme           | Dracula Pro                                         |                           |
| Package Manager | scoop                                               | CLI package manager       |
| Prompt          | oh-my-posh                                          | Prompt theming engine     |
| Config Repo     | https://github.com/Malemow/system-home/tree/windows | Windows shell config      |

---

### 4.3 Browser Extensions (Chrome)
---

| Extension        | Role / Description                |
|------------------|----------------------------------|
| 1Password        | Password manager                 |
| IDM              | Download manager                 |
| AdBlock          | Ad blocking                      |
| MetaMask         | Web3 wallet                      |
| Vimium           | Keyboard navigation              |
| 沉靜式翻譯        | Translation (ChatGPT API)        |
| 串改猴            | Userscripts manager              |
| iCloud 書籤       | Bookmark synchronization         |

> Role: Security, productivity, automation.


---

## 5. Hardware Inventory

### 5.1 Workstation (Primary PC)
---

| Hardware | Model                                                                                                                                                              |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| CPU      | [Intel i5-13400 [10;16]](https://www.intel.com.tw/content/www/tw/zh/products/sku/230495/intel-core-i513400-processor-20m-cache-up-to-4-60-ghz/specifications.html) |
| MB       | [MSI PRO B760M-A WIFI DDR4](https://tw.msi.com/Motherboard/PRO-B760M-A-WIFI-DDR4)                                                                                  |
| RAM 1    | [Kingston kit(16GB_2) DDR4-3600(KF436C18BBK2/32)(2048_8)](https://www.kingston.com/tw/memory/gaming/kingston-fury-beast-ddr4-rgb-memory)                           |
| RAM 2    | [Kingston kit(16GB_2) DDR4-3600(KF436C18BBK2/32)(2048_8)](https://www.kingston.com/tw/memory/gaming/kingston-fury-beast-ddr4-rgb-memory)                           |
| GPU      | [MSI RTX4060 VENTUS 2X WHITE 8G OC[萬圖師娘限量版](2505MHz/19.9cm/雙風扇)](https://tw.msi.com/Graphics-Card/GeForce-RTX-4060-VENTUS-2X-WHITE-8G-OC-VTS)                      |
| Cooler   | [MSI MAG CoreLiquid P240](https://tw.msi.com/Liquid-Cooling/MAG-CORELIQUID-P240)                                                                                   |
| Case     | [Montech SKY TWO White (GPT:40;CPU:16.8)](https://www.telon.com.tw/tc/products_detail.php?nid=307)                                                                 |
| PSU      | [SUPER FLOWER LEADEX III 750W (Gold)](https://www.super-flower.com.tw/zh-TW/products/leadex-iii-gold-750w)                                                         |

### 5.2 Mac
---

| Model          | Year |
| -------------- | ---- |
| MacBook Air M1 | 2020 |

### 5.3 Peripherals
---

#### Mouse

| Model                    | Note |
|--------------------------|------|
| Logitech G502 Hero       | Wired gaming mouse |
| Logitech G703            | Wireless gaming mouse |
| Logitech Pro Wireless    | Lightweight esports mouse |

#### Keyboard

| Model                                   | Note |
|-----------------------------------------|------|
| HHKB Hybrid Type-S (Snow)                | 60%, Topre, silent |
| HHKB Hybrid Type-S (White)               | 60%, Topre, silent |
| Logitech G913 White                     | Low-profile wireless |
| Logitech G915 White                     | Low-profile wireless |

#### Monitor

| Model        | Note |
|--------------|------|
| MSI MAG322CR | Curved gaming monitor |
| BenQ EL2870U | 4K monitor |

#### Graphics Tablet

| Model              | Note |
|--------------------|------|
| Wacom One (2017)   | Entry pen tablet |
| Wacom Cintiq 16    | Pen display |

### 5.4 Phone
---

| Model                  | Storage | Color |
|------------------------|---------|--------|
| iPhone 12              | 128G    | White  |
| iPhone 16              | 256G    | Teal   |

---

## 6. Software Stack

### macOS
---

| Software  | Role / Description                    |
|-----------|---------------------------------------|
| Raycast   | Launcher / automation                 |
| Warp      | Modern terminal                       |
| DeepL     | Translation                           |
| CyberDuck | SFTP / cloud browser                  |
| Fork      | Git GUI client                        |
| Buho      | System cleanup / maintenance          |
| Grid      | Window management / tiling            |

### Windows
---

| Software          | Role / Description                |
|-------------------|----------------------------------|
| IDM               | Download manager                 |
| AquaSnap          | Window tiling / snapping         |
| Wallpaper Engine  | Desktop enhancement              |
| PowerToys         | Windows productivity utilities   |
| MSI CPU-Z         | Hardware information / monitor   |
| AIDA64            | System diagnostics / benchmark   |

---

## 7. Note & Knowledge Management

- HackMD — Main architecture & ops documentation
- Obsidian — Knowledge base & personal notes
	- Repo: https://github.com/Malemow/Note

> Strategy: Draft and share on HackMD, archive and expand in Obsidian.

---

## 8. Operations Guide

### 8.1 General Principles
- Prefer automation and reproducibility
- All changes should be documented
- Backup before major upgrades

### 8.2 Add New Service Checklist
- Define role & owner
- Allocate VM / container
- Assign IP / DNS
- Add monitoring
- Update documentation

### 8.3 Upgrade Flow (Infra)
1. Snapshot / backup
2. Test on non-critical system
3. Perform upgrade
4. Validate services
5. Update change log

---

## 9. Change Log

| Date       | Component | Change Description |
|------------|-----------|--------------------|
| 2025-12-23 | Document  | Initial architecture draft |

---

## 10. Appendix

### 10.1 References
- https://github.com/Malemow
- Vendor official documentation