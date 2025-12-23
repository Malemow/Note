# 個人 IT 架構文件

> 擁有者：Nick  
> 範圍：Home-Lab 與個人開發環境  
> 最後更新：2025-12-23

> 資安聲明：  
> 本文件預計對外公開分享。  
> 內部網路相關細節（如 VLAN ID、IP 網段、位址規劃、  
> 防火牆規則與主機對應關係）已刻意省略，  
> 以避免暴露敏感基礎設施資訊。
---
- 🌏 [English](Detail.md)
## 1. 概覽

本文件描述我個人 IT 環境的整體架構、工具鏈與維運設計。  
目標如下：

- 提供清楚的系統全貌
- 支援可重建的環境與災難復原
- 作為長期維運參考文件
- 紀錄重要設計決策與變更

**設計原則**

- 單一閘道器，集中式路由與安全控管
- 分層式架構（Network / Server / Client）
- 以自動化與可觀測性優先
- 文件即程式（Documentation as Code）

---

## 2. 網路架構

### 2.1 拓樸

- ISP → UniFi UDM → LAN / VLANs → Servers / Clients
- Wi-Fi 用戶端透過 TP-Link AX50 連線（AP 模式）

### 2.2 網路設備

#### 閘道器
- 設備：UniFi UDM
- 說明：
  - 單一 L3 Gateway 設計
  - 集中式政策與安全控管

#### 無線基地台
- 設備：TP-Link AX50
- 模式：Bridge / AP 模式
- 角色：
  - 僅提供 L2 無線存取
- 說明：
  - 關閉路由與 DHCP
  - 避免雙重 NAT

### 2.3 邏輯分區（抽象）

內部網路依角色邏輯劃分為多個區域，例如：

- 基礎設施區（Infrastructure）
- 伺服器 / 服務區
- 用戶端區
- IoT / 不受信任區

透過閘道器上的 VLAN 與防火牆政策進行隔離控管。  
實際 VLAN ID 與網段刻意不在本文件中揭露。

---

## 3. 伺服器與服務

### 3.1 虛擬化與儲存

- ESXi v8.03u
	- vCenter v8.03u
- TrueNAS v25.10.0.1（Goldeye）

> 角色：VM 管理與儲存的核心基礎設施。

### 3.2 核心服務

- Nginx — 反向代理
- Grafana — 可觀測性平台
	- Loki — 日誌彙整
	- Alloy — 指標 / 日誌代理
- Line Bot — 記帳機器人
- Jump Host — SSH 入口主機
- Suwayomi — 漫畫伺服器
- Rsync Server — 備份（Rsync）
- DNS
	- DNSDist
	- PDNS Auth
	- PDNS Recursor

> 角色：內部服務、監控與安全存取。

---

## 4. 用戶端環境

### 4.1 IDE / 編輯器

#### JetBrains 工具鏈
- WebStorm — Web / 前端
- RustRover — Rust
- CLion — C / C++
- GoLand — Golang
- PhpStorm — PHP / Laravel
- Rider — C# / .NET
- DataGrip — 資料庫管理

> 角色：主要全功能 IDE 開發環境。

#### Neovim（客製化）

Repo: https://github.com/Malemow/neovim

核心能力：
- LSP 與補全：`lsp.lua`, `nvim-cmp.lua`
- 導覽與搜尋：`telescope.lua`, `grug-far.lua`, `aerial.lua`
- Git：`gitsigns.lua`, `lazygit.lua`
- UI/UX：`lualine.lua`, `noice.lua`, `bufferline.lua`, `mini-*`
- 除錯：`nvim-dap.lua`
- 檔案總管：`nvim-tree.lua`
- AI 輔助：`claudecode.lua`
- Tree-sitter：`treesitter.lua`

> 角色：輕量化、鍵盤導向、高度客製的編輯器。

---

### 4.2 終端環境

#### macOS
---

| 項目            | 工具 / 值                                      | 說明                          |
| --------------- | --------------------------------------------- | ----------------------------- |
| 終端機          | iTerm2                                        | 主要終端模擬器                |
| 套件管理        | Homebrew                                      | 套件管理                      |
| Shell           | zsh + oh-my-zsh                               | 互動式 shell 框架             |
| 主題            | Dracula Pro                                   |                               |
| 監控            | btop / ctop                                   | 系統與容器監控                |
| 檔案列表        | eza                                           | 現代化 `ls` 替代               |
| 搜尋            | fzf / ripgrep                                 | 模糊搜尋與 grep               |
| Repo 管理       | ghq                                           | Git 倉庫管理                  |
| 設定 Repo       | https://github.com/Malemow/system-home/tree/mac | macOS shell 設定              |

#### Windows
---

| 項目            | 工具 / 值                                          | 說明                      |
| --------------- | -------------------------------------------------- | ------------------------- |
| 終端機          | Windows Terminal                                   | 主要終端模擬器            |
| Shell           | PowerShell                                         | 預設 Windows shell        |
| 主題            | Dracula Pro                                        |                           |
| 套件管理        | scoop                                              | CLI 套件管理工具          |
| Prompt          | oh-my-posh                                         | Prompt 主題引擎           |
| 設定 Repo       | https://github.com/Malemow/system-home/tree/windows | Windows shell 設定        |

---

### 4.3 瀏覽器擴充套件（Chrome）
---

| 擴充套件        | 角色 / 說明                   |
|------------------|-------------------------------|
| 1Password        | 密碼管理器                    |
| IDM              | 下載管理工具                  |
| AdBlock          | 廣告阻擋                      |
| MetaMask         | Web3 錢包                     |
| Vimium           | 鍵盤導向瀏覽                  |
| 沉靜式翻譯        | 翻譯（ChatGPT API）            |
| 串改猴            | Userscripts 管理工具          |
| iCloud 書籤       | 書籤同步                      |

> 角色：資安、生產力、自動化。

---

## 5. 硬體清冊

### 5.1 工作站（主力 PC）
---

| 硬體 | 型號 |
|------|------|
| CPU | [Intel i5-13400 [10;16]](https://www.intel.com.tw/content/www/tw/zh/products/sku/230495/intel-core-i513400-processor-20m-cache-up-to-4-60-ghz/specifications.html) |
| MB | [MSI PRO B760M-A WIFI DDR4](https://tw.msi.com/Motherboard/PRO-B760M-A-WIFI-DDR4) |
| RAM 1 | [Kingston kit(16GB_2) DDR4-3600(KF436C18BBK2/32)(2048_8)](https://www.kingston.com/tw/memory/gaming/kingston-fury-beast-ddr4-rgb-memory) |
| RAM 2 | [Kingston kit(16GB_2) DDR4-3600(KF436C18BBK2/32)(2048_8)](https://www.kingston.com/tw/memory/gaming/kingston-fury-beast-ddr4-rgb-memory) |
| GPU | [MSI RTX4060 VENTUS 2X WHITE 8G OC【萬圖師娘限量版】](https://tw.msi.com/Graphics-Card/GeForce-RTX-4060-VENTUS-2X-WHITE-8G-OC-VTS) |
| Cooler | [MSI MAG CoreLiquid P240](https://tw.msi.com/Liquid-Cooling/MAG-CORELIQUID-P240) |
| Case | [Montech SKY TWO White](https://www.telon.com.tw/tc/products_detail.php?nid=307) |
| PSU | [SUPER FLOWER LEADEX III 750W (Gold)](https://www.super-flower.com.tw/zh-TW/products/leadex-iii-gold-750w) |

### 5.2 Mac
---

| 型號 | 年份 |
|------|------|
| MacBook Air M1 | 2020 |

### 5.3 周邊設備
---

#### 滑鼠

| 型號 | 說明 |
|------|------|
| Logitech G502 Hero | 有線電競滑鼠 |
| Logitech G703 | 無線電競滑鼠 |
| Logitech Pro Wireless | 輕量化電競滑鼠 |

#### 鍵盤

| 型號 | 說明 |
|------|------|
| HHKB Hybrid Type-S（Snow） | 60%、Topre、靜音 |
| HHKB Hybrid Type-S（White） | 60%、Topre、靜音 |
| Logitech G913 White | 低鍵程無線 |
| Logitech G915 White | 低鍵程無線 |

#### 螢幕

| 型號 | 說明 |
|------|------|
| MSI MAG322CR | 曲面電競螢幕 |
| BenQ EL2870U | 4K 螢幕 |

#### 繪圖板

| 型號 | 說明 |
|------|------|
| Wacom One (2017) | 入門繪圖板 |
| Wacom Cintiq 16 | 繪圖顯示器 |

### 5.4 手機
---

| 型號 | 容量 | 顏色 |
|------|------|------|
| iPhone 12 | 128G | White |
| iPhone 16 | 256G | Teal |

---

## 6. 軟體工具

### macOS
---

| 軟體 | 角色 / 說明 |
|------|--------------|
| Raycast | 啟動器 / 自動化 |
| Warp | 現代化終端機 |
| DeepL | 翻譯 |
| CyberDuck | SFTP / 雲端瀏覽 |
| Fork | Git GUI |
| Buho | 系統清理 / 維護 |
| Grid | 視窗管理 |

### Windows
---

| 軟體 | 角色 / 說明 |
|------|--------------|
| IDM | 下載管理 |
| AquaSnap | 視窗貼齊 |
| Wallpaper Engine | 桌面美化 |
| PowerToys | 生產力工具 |
| MSI CPU-Z | 硬體資訊 |
| AIDA64 | 系統診斷 / Benchmark |

---

## 7. 筆記與知識管理

- HackMD — 主要架構與維運文件
- Obsidian — 知識庫與個人筆記
	- Repo: https://github.com/Malemow/Note

> 策略：HackMD 撰寫與分享，Obsidian 彙整與擴充。

---

## 8. 維運指南

### 8.1 一般原則
- 優先自動化與可重現性
- 所有變更都需文件化
- 重大升級前先備份

### 8.2 新增服務檢查清單
- 定義角色與負責人
- 配置 VM / 容器
- 指派 IP / DNS
- 加入監控
- 更新文件

### 8.3 基礎設施升級流程
1. Snapshot / 備份
2. 於非關鍵系統測試
3. 執行升級
4. 驗證服務
5. 更新變更紀錄

---

## 9. 變更紀錄

| 日期 | 元件 | 說明 |
|------|------|------|
| 2025-12-23 | 文件 | 初版架構草稿 |

---

## 10. 附錄

### 10.1 參考
- https://github.com/Malemow
- 各廠商官方文件
