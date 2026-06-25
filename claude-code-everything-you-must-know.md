# Everything You Must Know About Claude Code
### Claude Code 完全操作指南 — 好好用 AI 補充教材

> **適用對象：** 想用 AI 輔助日常工作、程式開發與文件管理的辦公室工作者
> **學習目標：** 掌握 Claude Code CLI 工具的核心操作，讓 AI 成為你的高效工作夥伴

---

## 目錄

1. [什麼是 Claude Code？](#1-什麼是-claude-code)
2. [為什麼要用 Claude Code？](#2-為什麼要用-claude-code)
3. [安裝與初始設定](#3-安裝與初始設定)
4. [介面概覽與基本操作](#4-介面概覽與基本操作)
5. [斜線指令（Slash Commands）完整列表](#5-斜線指令slash-commands完整列表)
6. [鍵盤快捷鍵](#6-鍵盤快捷鍵)
7. [權限模式與安全控制](#7-權限模式與安全控制)
8. [記憶系統：CLAUDE.md 檔案](#8-記憶系統claudemd-檔案)
9. [MCP 伺服器擴充](#9-mcp-伺服器擴充)
10. [Hooks 自動化流程](#10-hooks-自動化流程)
11. [設定與個人化](#11-設定與個人化)
12. [IDE 整合：VS Code 與 JetBrains](#12-ide-整合vs-code-與-jetbrains)
13. [多代理人工作流程](#13-多代理人工作流程)
14. [Claude Code + AI 工具整合技巧](#14-claude-code--ai-工具整合技巧)
15. [常見錯誤與解決方式](#15-常見錯誤與解決方式)
16. [速查表 Cheat Sheet](#16-速查表-cheat-sheet)

---

## 1. 什麼是 Claude Code？

**Claude Code** 是 Anthropic 官方推出的 **AI 程式助手 CLI（命令列介面）**，讓你可以在終端機（Terminal）中直接與 Claude AI 對話，並讓 AI 幫你：

- 讀取、編輯、建立專案中的檔案
- 執行 Shell 指令與腳本
- 搜尋程式碼庫、查看 Git 歷史
- 撰寫、測試、除錯程式碼
- 管理 GitHub Issue、PR 等工作

```
你的終端機
     │
     ▼
Claude Code CLI ←→ Claude AI（雲端）
     │
     ▼
你的本地專案資料夾（讀取 / 修改檔案）
```

### Claude Code 可在哪裡使用？

| 平台 | 說明 |
|------|------|
| **終端機 CLI** | 直接在命令列輸入 `claude` 開啟 |
| **桌面應用程式** | Mac / Windows 原生應用（含 GUI） |
| **Web 應用** | claude.ai/code 網頁版 |
| **VS Code 擴充** | 整合於編輯器側欄 |
| **JetBrains 擴充** | 整合於 IntelliJ、PyCharm 等 IDE |

---

## 2. 為什麼要用 Claude Code？

### 與一般 Claude 網頁版的差異

| 功能 | Claude 網頁版 | Claude Code CLI |
|------|--------------|-----------------|
| 讀取本地檔案 | ❌ 需手動貼上 | ✅ 直接存取 |
| 修改檔案 | ❌ 需手動複製 | ✅ 自動寫入 |
| 執行指令 | ❌ 不行 | ✅ 可執行 Shell |
| 專案記憶 | ❌ 每次重來 | ✅ CLAUDE.md 持久記憶 |
| 工具擴充（MCP） | 有限 | ✅ 豐富的 MCP 生態 |
| Git 整合 | ❌ 需手動 | ✅ 原生支援 |

### 辦公室工作者的使用情境

```
📄 文件整理    → 批次重命名、整理資料夾結構
📊 資料分析    → 讀 CSV、產出分析報告
🔧 腳本自動化  → 寫 Python/Bash 腳本，讓重複工作消失
📝 程式碼審查  → 讀取整個專案，提供改善建議
🐛 除錯協助    → 貼錯誤訊息，AI 直接找到問題根源
📨 Git 工作流  → 自動寫 commit message、建立 PR
```

---

## 3. 安裝與初始設定

### 系統需求

- **Node.js 18+**（必要）
- **作業系統**：macOS、Windows、Linux

### 步驟一：安裝 Claude Code

```bash
# 全域安裝 Claude Code
npm install -g @anthropic-ai/claude-code

# 確認安裝成功
claude --version
```

> **Windows 使用者注意**：推薦在 WSL（Windows Subsystem for Linux）中使用，體驗更佳。

### 步驟二：登入驗證

```bash
# 啟動 Claude Code，首次會引導登入
claude

# 或直接登入
claude login
```

登入方式有兩種：
1. **Anthropic API Key**：在 `https://console.anthropic.com` 取得
2. **claude.ai 帳號**：直接使用瀏覽器 OAuth 登入（Pro/Max 方案）

### 步驟三：進入專案資料夾開始使用

```bash
# 進入你的專案資料夾
cd /path/to/your/project

# 啟動 Claude Code
claude
```

啟動後會出現互動式提示符，直接輸入自然語言即可開始工作。

---

## 4. 介面概覽與基本操作

### 基本互動模式

```
$ claude
╔══════════════════════════════════╗
║  Claude Code  v1.x.x             ║
║  Working directory: /your/project║
╚══════════════════════════════════╝

> 幫我整理這個資料夾的 README.md，讓它更清楚

● Claude 正在讀取 README.md...
● Claude 正在分析內容...
● Claude 正在編輯 README.md...
✓ 完成！
```

### 非互動模式（一次性指令）

```bash
# 直接執行單一任務，不進入互動模式
claude "幫我看看這個資料夾有哪些 Python 檔案"

# 處理管道（Pipe）輸入
cat error.log | claude "幫我解讀這個錯誤"

# 搭配輸出旗標
claude --output-format json "列出所有 .py 檔案"
```

### 常用指令旗標

```bash
# 指定工作目錄
claude --workspace /path/to/project

# 使用特定模型
claude --model claude-opus-4-8

# 啟用詳細輸出
claude --verbose

# 不使用顏色（適合寫入日誌）
claude --no-color

# 顯示說明
claude --help
```

---

## 5. 斜線指令（Slash Commands）完整列表

在 Claude Code 的互動模式中，輸入 `/` 開頭的指令可快速執行特定功能。

### 基本控制指令

| 指令 | 功能說明 |
|------|---------|
| `/help` | 顯示所有可用指令與說明 |
| `/clear` | 清除當前對話記錄，開始新對話 |
| `/exit` 或 `/quit` | 離開 Claude Code |
| `/status` | 顯示目前連線狀態、模型資訊 |

### 對話管理指令

| 指令 | 功能說明 |
|------|---------|
| `/compact` | 壓縮對話歷史，節省 token 用量（長對話必用） |
| `/resume` | 恢復上次對話 |
| `/history` | 查看對話歷史 |
| `/undo` | 撤銷上一個 AI 操作 |

### 計畫模式（Plan Mode）

| 指令 | 功能說明 |
|------|---------|
| `/plan` | 進入計畫模式，AI 先說明做什麼再執行 |
| `/approve` | 確認 AI 的計畫並開始執行 |
| `/reject` | 拒絕 AI 的計畫 |

> **計畫模式建議：** 執行重要或不可逆的操作前，先用 `/plan` 讓 AI 說明計畫。

### 程式碼審查指令

| 指令 | 功能說明 |
|------|---------|
| `/code-review` | 審查目前分支（branch）的程式碼變更 |
| `/code-review ultra` | 啟動多代理人深度審查（需 Pro 方案） |
| `/review` | 審查指定檔案或範圍 |

### 記憶與設定指令

| 指令 | 功能說明 |
|------|---------|
| `/memory` | 查看與管理記憶（CLAUDE.md 內容） |
| `/config` | 開啟設定介面 |
| `/login` | 切換或重新登入帳號 |
| `/logout` | 登出當前帳號 |
| `/model` | 查看或切換使用的 Claude 模型 |

### 工具與 MCP 指令

| 指令 | 功能說明 |
|------|---------|
| `/mcp` | 管理 MCP 伺服器連線 |
| `/tools` | 查看目前可用的工具列表 |

---

## 6. 鍵盤快捷鍵

### 對話控制

| 快捷鍵 | 功能 |
|--------|------|
| `Enter` | 送出訊息（單行） |
| `Shift + Enter` | 換行（多行輸入） |
| `↑` / `↓` | 瀏覽歷史輸入 |
| `Ctrl + C` | 中斷 AI 當前操作 |
| `Ctrl + D` | 離開 Claude Code |
| `Esc` | 取消當前輸入 |

### 快速執行

| 快捷鍵 | 功能 |
|--------|------|
| `Ctrl + L` | 清除終端機畫面（不清除對話） |
| `Ctrl + K` | 清除當前輸入行 |
| `Tab` | 自動補全指令或路徑 |

### 工具審核模式（需手動確認時）

| 快捷鍵 | 功能 |
|--------|------|
| `y` 或 `Enter` | 允許 AI 執行此操作 |
| `n` | 拒絕此操作 |
| `a` | 允許所有後續操作（本次對話） |
| `d` | 拒絕所有後續操作並停止 |

---

## 7. 權限模式與安全控制

Claude Code 有嚴格的權限控制機制，保護你的系統安全。

### 四種權限模式

```
模式 1：預設模式（Default）
  → 每次執行危險操作都需要你手動確認

模式 2：自動模式（Auto-approve）
  → 自動允許常見安全操作，減少確認次數
  → 啟動：claude --auto-approve

模式 3：完整信任模式（--dangerously-skip-permissions）
  → 跳過所有確認（⚠️ 謹慎使用！）
  → 適合：受信任的自動化腳本、CI/CD 環境

模式 4：唯讀模式（Read-only）
  → AI 只能讀取，不能修改任何檔案
  → 適合：程式碼審查、文件閱讀
```

### 需要確認的操作類型

| 操作類型 | 風險等級 | 說明 |
|---------|---------|------|
| 讀取檔案 | 🟢 低 | 通常自動允許 |
| 建立新檔案 | 🟡 中 | 需確認 |
| 編輯現有檔案 | 🟡 中 | 需確認 |
| 刪除檔案 | 🔴 高 | 強制確認 |
| 執行 Shell 指令 | 🔴 高 | 強制確認 |
| 推送 Git 變更 | 🔴 高 | 強制確認 |
| 安裝套件 | 🔴 高 | 強制確認 |

### 設定允許/禁止的工具

在 `.claude/settings.json` 中可以細緻控制：

```json
{
  "permissions": {
    "allow": [
      "Read",
      "Write",
      "Edit"
    ],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(sudo *)"
    ]
  }
}
```

---

## 8. 記憶系統：CLAUDE.md 檔案

**CLAUDE.md** 是 Claude Code 的「長期記憶」機制，讓 AI 在每次啟動時都能記住你的專案偏好與規則。

### CLAUDE.md 的位置層級

```
~/.claude/CLAUDE.md          ← 全域設定（適用所有專案）
~/projects/myapp/CLAUDE.md   ← 專案級設定（推薦）
~/projects/myapp/src/CLAUDE.md ← 子目錄設定
```

### CLAUDE.md 寫什麼？

```markdown
# 我的專案 CLAUDE.md

## 專案說明
這是一個使用 Python + FastAPI 的後端 API 專案。

## 開發規範
- 所有函數必須有型別標注（Type Hints）
- 變數命名使用 snake_case
- 每個函數都要有 docstring
- 使用繁體中文撰寫註解

## 常用指令
- 啟動開發伺服器：`uvicorn main:app --reload`
- 執行測試：`pytest tests/`
- 格式化程式碼：`black .`

## 禁止事項
- 不要直接修改 production 環境的設定
- 不要刪除 tests/ 資料夾內的檔案

## 常見問題
- 資料庫連線設定在 .env 檔案中
- 靜態檔案放在 static/ 資料夾
```

### 管理記憶的指令

```bash
# 在 Claude Code 中查看目前記憶
/memory

# 讓 Claude 更新記憶
> 請把「使用 Black 格式化程式碼」加入記憶

# 直接編輯 CLAUDE.md
/memory edit
```

---

## 9. MCP 伺服器擴充

**MCP（Model Context Protocol）** 是一個開放協定，讓 Claude Code 可以連接各種外部工具與服務。

### 常用 MCP 伺服器

| MCP 伺服器 | 功能 | 使用情境 |
|-----------|------|---------|
| `@anthropic/mcp-github` | GitHub 操作 | 建立 Issue、PR、讀取 repo |
| `@anthropic/mcp-filesystem` | 擴充檔案存取 | 存取不同磁碟分區 |
| `@anthropic/mcp-brave-search` | 網路搜尋 | 查詢最新資訊 |
| `@anthropic/mcp-sqlite` | SQLite 資料庫 | 查詢與管理本地資料庫 |
| `@anthropic/mcp-puppeteer` | 瀏覽器自動化 | 網路爬蟲、測試網頁 |
| `@anthropic/mcp-slack` | Slack 整合 | 發送訊息、查詢頻道 |

### 安裝與設定 MCP 伺服器

**方法一：透過 CLI 設定**

```bash
# 新增 MCP 伺服器（以 GitHub 為例）
claude mcp add @anthropic/mcp-github

# 列出已安裝的 MCP 伺服器
claude mcp list

# 移除 MCP 伺服器
claude mcp remove @anthropic/mcp-github
```

**方法二：手動編輯設定檔**

在 `~/.claude/settings.json` 中：

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-github"],
      "env": {
        "GITHUB_TOKEN": "your-github-token-here"
      }
    },
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your-brave-api-key"
      }
    }
  }
}
```

### 在對話中使用 MCP 工具

```
# 安裝 GitHub MCP 後，可以這樣使用：
> 幫我查看 anthropics/claude-code 這個 repo 最近的 Issues

> 幫我建立一個標題為「修復登入 Bug」的 Issue，指派給 alice

> 幫我列出所有 open 狀態的 PR
```

---

## 10. Hooks 自動化流程

**Hooks** 讓你可以在 Claude Code 的特定事件發生時，自動執行自訂腳本。

### Hooks 的觸發時機

| 事件名稱 | 觸發時機 |
|---------|---------|
| `PreToolUse` | 在 AI 執行任何工具之前 |
| `PostToolUse` | 在 AI 執行工具之後 |
| `Stop` | 當 AI 完成任務後 |
| `SubagentStop` | 子代理人任務完成後 |
| `Notification` | 有通知事件時 |

### 設定 Hooks

在 `.claude/settings.json` 中設定：

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "echo '檔案已修改，執行格式化...' && black ."
          }
        ]
      }
    ],
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "notify-send 'Claude Code' 'AI 任務完成！'"
          }
        ]
      }
    ]
  }
}
```

### 實用 Hooks 範例

**範例一：自動格式化程式碼**
```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "black . && isort ."
          }
        ]
      }
    ]
  }
}
```

**範例二：儲存操作日誌**
```json
{
  "hooks": {
    "PostToolUse": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo \"$(date): 工具使用\" >> ~/.claude/activity.log"
          }
        ]
      }
    ]
  }
}
```

**範例三：任務完成通知（macOS）**
```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "osascript -e 'display notification \"任務完成！\" with title \"Claude Code\"'"
          }
        ]
      }
    ]
  }
}
```

---

## 11. 設定與個人化

### 設定檔位置

```
~/.claude/settings.json     ← 個人全域設定
.claude/settings.json       ← 專案設定（放在專案根目錄）
.claude/settings.local.json ← 本機專案設定（不加入 git）
```

### 常用設定項目

```json
{
  "model": "claude-opus-4-8",
  "theme": "dark",
  "language": "zh-TW",
  "autoApprove": false,
  "verbose": false,
  "permissions": {
    "allow": ["Read", "Write", "Edit", "Bash"],
    "deny": ["Bash(sudo *)"]
  },
  "env": {
    "ANTHROPIC_API_KEY": "your-api-key"
  }
}
```

### 環境變數設定

```bash
# 設定 API Key（推薦放在 shell 設定檔，如 ~/.bashrc 或 ~/.zshrc）
export ANTHROPIC_API_KEY="your-api-key-here"

# 指定預設模型
export CLAUDE_MODEL="claude-opus-4-8"

# 設定 MCP 服務的 Token
export GITHUB_TOKEN="your-github-token"
```

### 切換模型

```bash
# 在對話中切換
/model claude-sonnet-4-6

# 啟動時指定
claude --model claude-sonnet-4-6
```

---

## 12. IDE 整合：VS Code 與 JetBrains

### VS Code 整合

**安裝方式**

```bash
# 從 VS Code 擴充市場安裝「Claude Code」擴充
# 或在 VS Code 內按 Ctrl+Shift+X 搜尋「Claude Code」
```

**主要功能**

| 功能 | 說明 |
|------|------|
| 側欄對話面板 | 不需切換視窗，直接在 IDE 裡對話 |
| 程式碼高亮選取 | 選取程式碼後右鍵 → 傳送給 Claude |
| 內嵌程式碼修改 | AI 直接在編輯器中修改程式碼 |
| 終端機整合 | 可在 VS Code 終端執行 `claude` |
| 診斷訊息整合 | 讀取 VS Code 的錯誤/警告訊息 |

**在 VS Code 中使用技巧**

```
1. 選取有問題的程式碼
2. 右鍵 → "Ask Claude"
3. 輸入問題，例如：「這段程式碼有什麼問題？」
4. Claude 直接在編輯器提供修改建議
```

### JetBrains 整合

**支援的 IDE**
- IntelliJ IDEA
- PyCharm
- WebStorm
- GoLand
- Rider（C#）

**安裝方式**

```
1. 開啟 IDE
2. Settings → Plugins → Marketplace
3. 搜尋「Claude Code」
4. 安裝並重啟
```

**主要功能**

| 功能 | 說明 |
|------|------|
| 工具視窗 | 右側欄開啟 Claude 對話 |
| 程式碼意圖（Intentions） | Alt+Enter 時顯示 Claude 建議 |
| 整合式終端機 | 在 IDE 終端執行 Claude Code CLI |
| 語言感知 | 理解 Java/Python/Kotlin 語言結構 |

---

## 13. 多代理人工作流程

Claude Code 支援**多代理人（Multi-Agent）**架構，讓多個 AI 同時執行不同子任務，大幅提升效率。

### 什麼時候使用多代理人？

```
✅ 適合情境：
  → 需要同時處理多個獨立任務
  → 任務可以拆分成互相不干擾的子任務
  → 大型程式碼審查（不同 AI 審查不同面向）

❌ 不適合情境：
  → 任務有順序相依性
  → 修改同一個檔案的任務
  → 資源有限時（Token 用量會翻倍）
```

### /code-review ultra：深度程式碼審查

這是 Claude Code 內建的多代理人功能，用多個 AI 從不同角度審查程式碼：

```bash
# 審查目前 git branch 的所有變更
/code-review ultra

# 審查特定 GitHub PR
/code-review ultra 123

# 審查完成後，會產生詳細的審查報告
```

**審查涵蓋面向：**
- 安全性漏洞（SQL injection、XSS 等）
- 效能問題
- 程式碼風格與可讀性
- 測試覆蓋率
- 文件完整性

### 手動觸發子代理人

```bash
# 在對話中要求 AI 使用子代理人
> 請同時幫我：
> 1. 審查 auth.py 的安全性
> 2. 檢查 database.py 的效能問題
> 3. 更新 README.md 的安裝說明
> 用子代理人平行處理這三個任務

# Claude 會自動建立三個平行任務
```

---

## 14. Claude Code + AI 工具整合技巧

### 善用 CLAUDE.md 建立 AI 工作指南

```markdown
# 我的工作 CLAUDE.md（範本）

## 身份與目標
你是我的 AI 工作夥伴，幫助我更高效地完成開發工作。

## 工作語言
- 與我對話請使用繁體中文
- 程式碼內的變數/函數名稱使用英文
- 程式碼內的註解使用繁體中文

## 程式碼規範
- Python：遵循 PEP 8，必須有 Type Hints
- JavaScript：使用 ES2022+，Prettier 格式化
- 測試覆蓋率：新功能必須有對應測試

## 版本控制習慣
- Commit message 格式：`[類型] 簡短說明`
  - 類型：feat/fix/docs/refactor/test
  - 範例：`[feat] 新增使用者登入功能`
- 每個 PR 不超過 300 行變更

## 禁止操作
- 不要修改 .env 和 .env.production
- 不要刪除 migrations/ 資料夾
- 不要直接 push 到 main 分支
```

### 結合 Markdown 提升提示詞品質

```markdown
# 給 Claude Code 的有效提示詞模板

## 1. 任務說明型
> **目標**：重構 `user_service.py`
> **背景**：這個檔案負責使用者認證，目前程式碼難以維護
> **要求**：
> - 拆分成更小的函數
> - 加入適當的錯誤處理
> - 保持原有功能不變
> **限制**：不要更動資料庫 schema

## 2. 問題排查型
> **問題**：執行 `python main.py` 出現以下錯誤：
> ```
> AttributeError: 'NoneType' object has no attribute 'id'
> ```
> **已嘗試**：重啟伺服器、清除快取
> **環境**：Python 3.11、FastAPI 0.104

## 3. 功能開發型
> 幫我在 `api/routes.py` 新增一個端點：
> - 路徑：`POST /api/users/reset-password`
> - 功能：發送密碼重設郵件
> - 輸入：`{"email": "user@example.com"}`
> - 輸出：`{"message": "已發送重設郵件"}`
```

### Claude Code 與 Git 的最佳工作流

```bash
# 1. 開始新功能前，讓 AI 幫你規劃
> 我要開發「忘記密碼」功能，請幫我分析需要修改哪些檔案

# 2. 開發過程中，讓 AI 幫你寫 commit message
> 我剛才的修改是新增密碼重設 API，幫我寫一個 commit message

# 3. 提交前，讓 AI 做最後審查
> 請審查我這次的所有修改，確認沒有安全疑慮

# 4. 建立 PR 前，讓 AI 幫你寫說明
> 幫我寫這個 PR 的說明，包含：修改內容、測試方式、注意事項
```

### 與 Marp 和 VS Code 的協作流程

```
1. 用 Claude Code 生成資料
   → claude "從 sales_data.csv 整理出本月銷售摘要"

2. 用 Claude 產出 Marp 簡報草稿
   → claude "把剛才的摘要做成 Marp 格式的簡報"

3. 在 VS Code 中預覽 Marp
   → 開啟 VS Code，用 Marp 擴充套件即時預覽

4. 用 Claude 優化簡報內容
   → "這份簡報的第三頁數據呈現方式不夠清楚，幫我改善"
```

---

## 15. 常見錯誤與解決方式

### 安裝與啟動問題

❌ **錯誤：`command not found: claude`**

```bash
# 問題：npm 全域路徑未設定
# 解決：
echo $PATH  # 確認 npm 全域路徑是否在其中

# macOS/Linux 修正：
export PATH="$HOME/.npm-global/bin:$PATH"
# 加入 ~/.bashrc 或 ~/.zshrc

# 或重新安裝：
npm install -g @anthropic-ai/claude-code --prefix ~/.npm-global
```

❌ **錯誤：`Node.js version is too old`**

```bash
# 問題：Node.js 版本低於 18
# 解決：更新 Node.js

# 使用 nvm（推薦）：
nvm install 20
nvm use 20

# 驗證：
node --version  # 應顯示 v20.x.x 以上
```

### 認證問題

❌ **錯誤：`Authentication failed` 或 `Invalid API key`**

```bash
# 檢查 API Key 是否正確設定
echo $ANTHROPIC_API_KEY

# 重新登入
claude login

# 手動設定 API Key
export ANTHROPIC_API_KEY="sk-ant-..."

# 確認 Key 在 settings.json 中（若有設定）
cat ~/.claude/settings.json
```

❌ **錯誤：`Rate limit exceeded`**

⚠️ 說明：你的 API 請求太頻繁，超過使用限制

💡 解決：
- 等待 1-5 分鐘後再試
- 使用 `/compact` 壓縮對話，減少 token 用量
- 升級 Anthropic 帳號方案

### 操作相關問題

❌ **錯誤：`Permission denied` 當 Claude 嘗試修改檔案**

```bash
# 問題：目錄或檔案沒有寫入權限
# 解決：
ls -la  # 查看權限
chmod 755 your_directory  # 給予適當權限
# 或以正確的使用者身份執行
```

⚠️ **警告：Claude 修改了錯誤的檔案**

💡 預防措施：
1. 在 CLAUDE.md 中明確列出禁止修改的檔案
2. 重要操作前使用 `/plan` 模式
3. 使用 git 追蹤，隨時可以 `git diff` 確認變更
4. 設定 `.claude/settings.json` 的 `deny` 清單

❌ **錯誤：MCP 伺服器連線失敗**

```bash
# 1. 確認 MCP 伺服器已安裝
claude mcp list

# 2. 測試 MCP 指令
npx @anthropic/mcp-github --version

# 3. 確認環境變數
echo $GITHUB_TOKEN

# 4. 重新安裝 MCP 伺服器
claude mcp remove github
claude mcp add @anthropic/mcp-github
```

### Token 與效能問題

⚠️ **對話變慢或 Context 不足**

💡 解決方案：

```bash
# 1. 壓縮對話歷史
/compact

# 2. 開始全新對話
/clear

# 3. 對大型檔案，只傳遞相關部分
> 這個函數（第 50-80 行）有問題，請幫我看看：
> [貼上相關程式碼]

# 4. 使用更精準的指示，減少來回次數
# ❌ 不好：「幫我修改這個檔案」
# ✅ 好：「幫我修改 user_service.py 第 45 行，把 None 改成 []」
```

---

## 16. 速查表 Cheat Sheet

```
═══════════════════════════════════════════════════════
  Claude Code 速查表 | 好好用 AI 補充教材
═══════════════════════════════════════════════════════

【安裝】
  npm install -g @anthropic-ai/claude-code
  claude --version                   確認版本
  claude login                       登入帳號

【啟動方式】
  claude                             互動模式（常用）
  claude "任務說明"                   一次性模式
  claude --auto-approve              自動批准模式
  cat file.txt | claude "分析這個"   管道輸入

【斜線指令】
  /help                              顯示所有指令
  /clear                             清除對話
  /compact                           壓縮對話（省 token）
  /plan                              計畫模式（先說再做）
  /memory                            查看記憶設定
  /config                            開啟設定
  /model claude-opus-4-8             切換模型
  /code-review                       審查程式碼
  /code-review ultra                 多代理人深度審查
  /mcp                               管理 MCP 工具

【鍵盤快捷鍵】
  Shift+Enter                        多行輸入
  Ctrl+C                             中斷 AI 操作
  Ctrl+D                             離開 Claude Code
  ↑/↓                                瀏覽輸入歷史
  y / n / a / d                      允許/拒絕操作

【設定檔位置】
  ~/.claude/settings.json            全域設定
  .claude/settings.json              專案設定
  CLAUDE.md（根目錄）                AI 長期記憶

【MCP 伺服器】
  claude mcp add @anthropic/mcp-github    新增 GitHub
  claude mcp list                          列出已安裝
  claude mcp remove github                 移除

【常用工作流程】
  1. cd /your/project && claude
  2. 設定 CLAUDE.md 告訴 AI 你的專案規則
  3. 讓 AI 閱讀專案：「幫我了解這個專案的結構」
  4. 開始工作：「幫我新增一個 XX 功能」
  5. 審查變更：git diff 或 /code-review
  6. 有問題隨時 Ctrl+C 中斷

【提示詞技巧】
  ❌ 模糊：「幫我修改這個專案」
  ✅ 精確：「幫我在 app.py 第 30 行新增錯誤處理」
  
  ❌ 太短：「有 bug」
  ✅ 完整：「執行 python main.py 出現 AttributeError，
             錯誤在 line 45，請幫我修復」

═══════════════════════════════════════════════════════
```

---

## 延伸學習資源

| 資源 | 連結 | 說明 |
|------|------|------|
| Claude Code 官方文件 | https://docs.anthropic.com/claude-code | 最完整的 API 與功能說明 |
| Anthropic Academy | https://anthropic.com/academy | 官方 AI 學習平台 |
| MCP 生態系 | https://modelcontextprotocol.io | MCP 伺服器列表與文件 |
| GitHub - Claude Code | https://github.com/anthropics/claude-code | 原始碼與 Issues |
| 好好用 AI 課程 | https://allenintaipei.github.io/ai-literacy-course-zh/ | 本補充教材所屬課程 |

---

*本教材為「好好用 AI」課程補充教材 | CC BY-SA 4.0 | 2026*
