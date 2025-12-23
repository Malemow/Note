# Windows 開發環境設定指南

## 目錄
- [前置條件](#前置條件)
- [Windows Terminal 設定](#windows-terminal-設定)
- [套件管理器安裝](#套件管理器安裝)
- [基礎工具安裝](#基礎工具安裝)
- [開發環境設定](#開發環境設定)
- [完整的 user_profile.ps1 設定](#完整的-userprofileps1-設定)
- [重新載入 PowerShell](#重新載入-powershell)
- [快速安裝腳本](#快速安裝腳本)
- [疑難排解](#疑難排解)
- [額外資源](#額外資源)

## 前置條件

在開始之前，請先完成以下準備工作：

1. 從 `Microsoft Store` 下載並安裝 **PowerShell 7+**
2. 從 `Microsoft Store` 下載並安裝 **Windows Terminal**
3. 下載並安裝 [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts) 字型
   - 推薦：JetBrainsMono Nerd Font、FiraCode Nerd Font

> **提示**：可以使用 Scoop 安裝 Nerd Fonts：
> ```powershell
> scoop bucket add nerd-fonts
> scoop install JetBrainsMono-NF
> ```

## Windows Terminal 設定

開啟 Windows Terminal 設定（`Ctrl + ,`）並調整以下項目：

- **預設值** → **外觀** → **色彩配置**：`Dracula Pro`
- **預設值** → **外觀** → **字體**：`JetBrainsMono Nerd Font` 或您偏好的 Nerd Font

## 套件管理器安裝

### 安裝 [Scoop](https://scoop.sh/)

Scoop 是 Windows 上的套件管理器，類似於 Linux 的 apt 或 macOS 的 Homebrew。

```powershell
# 設定執行政策
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# 下載並安裝 Scoop
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

驗證安裝：
```powershell
scoop --version
```

## 基礎工具安裝

安裝常用的命令列工具：

```powershell
# 基礎工具套件
scoop install curl sudo jq btop neovim gcc
```

**套件說明：**
- `curl` - 資料傳輸工具
- `sudo` - 提權執行命令
- `jq` - JSON 處理工具
- `btop` - 系統資源監控工具
- `neovim` - 現代化的文字編輯器
- `gcc` - GNU C/C++ 編譯器

## 開發環境設定

### Git 設定

```powershell
# 安裝 Git
scoop install git

# 下載並套用自訂 Git 設定檔
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/.gitconfig" -OutFile "$HOME\.gitconfig"
```

驗證安裝：
```powershell
git --version
git config --list
```

### Fastfetch 設定

Fastfetch 是一個快速的系統資訊顯示工具。

```powershell
# 安裝 Fastfetch
scoop install fastfetch

# 建立設定目錄
New-Item -ItemType Directory -Path "$HOME\.config\fastfetch" -Force

# 下載自訂設定檔
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/fastfetch_config.jsonc" -OutFile "$HOME\.config\fastfetch\config.jsonc"
```

測試執行：
```powershell
fastfetch
```

### PowerShell Profile 設定

建立自訂的 PowerShell 設定檔以載入個人化設定：

```powershell
# 建立設定目錄
New-Item -ItemType Directory -Path "$HOME\.config\powershell" -Force

# 建立自訂設定檔
New-Item -ItemType File -Path "$HOME\.config\powershell\user_profile.ps1" -Force

# 將自訂設定檔掛載到 PowerShell Profile
$profileLine = '. $env:USERPROFILE\.config\powershell\user_profile.ps1'
if (-not (Select-String -Path $PROFILE.CurrentUserCurrentHost -Pattern ([regex]::Escape($profileLine)) -Quiet -ErrorAction SilentlyContinue)) {
    Add-Content -Path $PROFILE.CurrentUserCurrentHost -Value $profileLine
}
```

確認設定：
```powershell
# 檢查 Profile 內容
Get-Content $PROFILE.CurrentUserCurrentHost
```

### Oh My Posh 設定

Oh My Posh 是一個跨平台的終端機提示符主題引擎。

```powershell
# 安裝 Oh My Posh
scoop install oh-my-posh

# 下載 Dracula 自訂主題設定
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/malemow_dracule.omp.toml" -OutFile "$HOME\.config\powershell\malemow_dracule.omp.toml"
```

測試 Oh My Posh：
```powershell
oh-my-posh init pwsh --config "$HOME\.config\powershell\malemow_dracule.omp.toml" | Invoke-Expression
```

### Node.js 版本管理器 (NVM)

```powershell
# 安裝 NVM for Windows
scoop install nvm

# 安裝最新的 Node.js LTS 版本
nvm install lts
nvm use lts
```

驗證安裝：
```powershell
node --version
npm --version
```

### Claude Code 安裝

Claude Code 是 Anthropic 官方的 AI 程式開發助手 CLI 工具。

```powershell
# 使用 npm 全域安裝 Claude Code
npm install -g @anthropic-ai/claude-code
```

驗證安裝：
```powershell
claude --version
```

初次使用設定：
```powershell
# 啟動 Claude Code（首次使用會引導你進行設定）
claude

# 或直接在專案目錄中使用
cd your-project
claude
```

**使用提示：**
- Claude Code 需要 Anthropic API Key，首次使用時會提示設定
- 支援多種 IDE 整合（VS Code、Cursor 等）
- 可用於程式碼審查、除錯、重構等開發任務

### PowerShell 增強模組

安裝所有必要的 PowerShell 模組：

```powershell
# 終端機圖示支援
Install-Module -Name Terminal-Icons -Repository PSGallery -Scope CurrentUser -Force

# Git 整合
Install-Module -Name posh-git -Scope CurrentUser -Force

# Windows 通知支援
Install-Module -Name BurntToast -Scope CurrentUser -Force

# 智慧目錄跳轉（可選）
Install-Module -Name z -Scope CurrentUser -Force
```

**模組說明：**
- `Terminal-Icons` - 為檔案和資料夾顯示圖示
- `posh-git` - Git 狀態顯示與自動補全
- `BurntToast` - Windows 10/11 通知功能
- `z` - 根據使用頻率智慧跳轉目錄

#### PSReadLine - 智慧自動補全

PSReadLine 提供強大的命令列編輯和歷史記錄功能：

```powershell
# 安裝 PSReadLine 預覽版本
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

將以下設定加入 `user_profile.ps1`：
```powershell
# PSReadLine 設定
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView
Set-PSReadLineOption -EditMode Windows
Set-PSReadLineOption -BellStyle None
```

#### FZF - 模糊搜尋工具

FZF 提供強大的互動式模糊搜尋功能：

```powershell
# 安裝相關工具
scoop install fzf ripgrep peco mingw make

# 安裝 PowerShell 整合模組
Install-Module -Name PSFzf -Scope CurrentUser -Force
```

將以下設定加入 `user_profile.ps1`：
```powershell
# FZF 設定
Import-Module PSFzf
Set-PsFzfOption -PSReadlineChordProvider 'Ctrl+f' -PSReadlineChordReverseHistory 'Ctrl+r'
```

**快捷鍵說明：**
- `Ctrl + f` - 搜尋檔案
- `Ctrl + r` - 搜尋命令歷史記錄

## 完整的 user_profile.ps1 設定

### 方法一：自動下載設定檔

使用預先設定好的設定檔：

```powershell
# 下載完整的設定檔
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/user_profile.ps1" -OutFile "$HOME\.config\powershell\user_profile.ps1"
```

### 方法二：手動設定

完整的 `user_profile.ps1` 內容範例：

```powershell
# ===== 模組載入 =====
Import-Module posh-git
Import-Module Terminal-Icons
Import-Module BurntToast

# ===== Oh My Posh 主題設定 =====
function Get-ScriptDirectory { Split-Path $MyInvocation.ScriptName }
$PROMPT_CONFIG = Join-Path (Get-ScriptDirectory) "malemow_dracule.omp.toml"
oh-my-posh init pwsh --config $PROMPT_CONFIG | Invoke-Expression

# ===== PSReadLine 設定 =====
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineOption -BellStyle None
Set-PSReadLineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView

# ===== FZF 模糊搜尋設定 =====
Import-Module PSFzf
Set-PsFzfOption -PSReadlineChordProvider 'Ctrl+f' -PSReadlineChordReverseHistory 'Ctrl+r'

# ===== 實用函數 =====
function which ($command) {
    Get-Command -Name $command -ErrorAction SilentlyContinue |
        Select-Object -ExpandProperty Path -ErrorAction SilentlyContinue
}

# ===== 別名設定 =====
Set-Alias vim nvim
Set-Alias ll ls
Set-Alias grep findstr
Set-Alias tig "$env:USERPROFILE\scoop\apps\git\current\usr\bin\tig.exe"
Set-Alias less "$env:USERPROFILE\scoop\apps\git\current\usr\bin\less.exe"

# ===== 環境變數 =====
$env:EDITOR = "nvim"
$env:VISUAL = "nvim"
$env:CLAUDE_CODE_GIT_BASH_PATH = "$env:USERPROFILE\scoop\apps\git\current\bin\bash.exe"

# ===== 啟動顯示（可選）=====
# fastfetch
```

## 重新載入 PowerShell

完成所有設定後，重新載入 PowerShell：

```powershell
. $PROFILE
```

或直接重新啟動 Windows Terminal。

## 快速安裝腳本

### 方法一：直接執行 Gist 腳本（推薦）

**最簡單的方式**，直接下載並執行安裝腳本：

```powershell
# 下載並執行一鍵安裝腳本
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/install-windows-dev-env.ps1" -OutFile "$env:TEMP\install-dev.ps1"; & "$env:TEMP\install-dev.ps1"
```

或者分步執行：

```powershell
# 1. 下載腳本
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/install-windows-dev-env.ps1" -OutFile "install-dev.ps1"

# 2. 檢視腳本內容（建議）
Get-Content install-dev.ps1

# 3. 執行安裝
.\install-dev.ps1
```

### 方法二：手動複製腳本

如果你想要自訂安裝內容，可以複製以下腳本：

```powershell
# 設定執行政策
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# 安裝 Scoop
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression

# 安裝基礎工具
scoop install curl sudo jq btop neovim gcc git oh-my-posh nvm fzf ripgrep peco mingw make fastfetch

# 安裝 Node.js（透過 NVM）
nvm install lts
nvm use lts

# 安裝 Claude Code
npm install -g @anthropic-ai/claude-code

# 安裝 PowerShell 模組
Install-Module -Name Terminal-Icons -Repository PSGallery -Scope CurrentUser -Force
Install-Module -Name posh-git -Scope CurrentUser -Force
Install-Module -Name BurntToast -Scope CurrentUser -Force
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
Install-Module -Name PSFzf -Scope CurrentUser -Force

# 建立設定目錄
New-Item -ItemType Directory -Path "$HOME\.config\powershell" -Force
New-Item -ItemType Directory -Path "$HOME\.config\fastfetch" -Force

# 下載設定檔
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/.gitconfig" -OutFile "$HOME\.gitconfig"
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/user_profile.ps1" -OutFile "$HOME\.config\powershell\user_profile.ps1"
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/malemow_dracule.omp.toml" -OutFile "$HOME\.config\powershell\malemow_dracule.omp.toml"
Invoke-WebRequest -Uri "https://gist.githubusercontent.com/Malemow/465f1f86c269783d27c9ee15c81627cc/raw/cb7b97154c6055c8c9c7f34e1e5a652145d61bce/fastfetch_config.jsonc" -OutFile "$HOME\.config\fastfetch\config.jsonc"

# 掛載 Profile
$profileLine = '. $env:USERPROFILE\.config\powershell\user_profile.ps1'
if (-not (Select-String -Path $PROFILE.CurrentUserCurrentHost -Pattern ([regex]::Escape($profileLine)) -Quiet -ErrorAction SilentlyContinue)) {
    Add-Content -Path $PROFILE.CurrentUserCurrentHost -Value $profileLine
}

Write-Host "✓ 安裝完成！請重新啟動 Windows Terminal。" -ForegroundColor Green
Write-Host "`n已安裝工具：" -ForegroundColor Cyan
Write-Host "  - Scoop 套件管理器" -ForegroundColor White
Write-Host "  - Git, Neovim, 及其他開發工具" -ForegroundColor White
Write-Host "  - Node.js (透過 NVM)" -ForegroundColor White
Write-Host "  - Claude Code CLI" -ForegroundColor White
Write-Host "  - Oh My Posh 美化終端機" -ForegroundColor White
Write-Host "`n下次啟動 Terminal 後，執行 'claude' 開始使用 Claude Code！" -ForegroundColor Yellow
```

## 疑難排解

### 執行政策問題

如果遇到執行政策錯誤，請執行：
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 模組載入失敗

檢查已安裝的模組：
```powershell
Get-Module -ListAvailable
```

更新 PowerShellGet：
```powershell
Install-Module -Name PowerShellGet -Force -AllowClobber
```

### Scoop 安裝失敗

確認網路連線並嘗試：
```powershell
scoop update
scoop checkup
```

### Oh My Posh 主題無法載入

確認主題檔案是否存在：
```powershell
Test-Path "$HOME\.config\powershell\malemow_dracule.omp.toml"
```

### Nerd Font 圖示無法顯示

1. 確認已安裝 Nerd Font 字型
2. 在 Windows Terminal 設定中選擇正確的字型
3. 重新啟動 Windows Terminal

### Claude Code 無法執行

若執行 `claude` 命令時出現「找不到命令」錯誤：

```powershell
# 檢查 Node.js 是否正確安裝
node --version
npm --version

# 檢查全域 npm 套件路徑
npm config get prefix

# 重新安裝 Claude Code
npm install -g @anthropic-ai/claude-code

# 確認安裝
claude --version
```

若仍無法執行，可能需要將 npm 全域套件路徑加入環境變數 PATH。

### NVM 切換版本後 npm 套件消失

這是正常現象，每個 Node.js 版本都有獨立的全域套件。切換版本後需重新安裝：

```powershell
npm install -g @anthropic-ai/claude-code
```

## 額外資源

### 套件管理與工具
- [Scoop 官方文件](https://scoop.sh/)
- [Scoop 套件搜尋](https://scoop.sh/#/apps)
- [NVM for Windows](https://github.com/coreybutler/nvm-windows)

### 終端機美化
- [Oh My Posh 主題](https://ohmyposh.dev/docs/themes)
- [Nerd Fonts 下載](https://www.nerdfonts.com/)
- [Dracula 主題](https://draculatheme.com/)

### PowerShell
- [PowerShell Gallery](https://www.powershellgallery.com/)
- [PSReadLine 文件](https://github.com/PowerShell/PSReadLine)
- [PSFzf 使用指南](https://github.com/kelleyma49/PSFzf)

### 開發工具
- [Claude Code 官方文件](https://github.com/anthropics/claude-code)
- [Neovim 官網](https://neovim.io/)
- [Fastfetch GitHub](https://github.com/fastfetch-cli/fastfetch)