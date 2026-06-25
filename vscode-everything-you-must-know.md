# Everything You Must Know About VS Code
### VS Code 完全指南 — 好好用 AI 補充教材

> **適用對象：** 辦公室工作者、文件撰寫者、AI 工具使用者  
> **學習目標：** 掌握 VS Code 核心功能，讓它成為你最強的文字與程式編輯工具

---

## 目錄

1. [什麼是 VS Code？](#1-什麼是-vs-code)
2. [為什麼選擇 VS Code？](#2-為什麼選擇-vs-code)
3. [安裝與初始設定](#3-安裝與初始設定)
4. [介面全覽](#4-介面全覽)
5. [檔案與資料夾管理](#5-檔案與資料夾管理)
6. [編輯技巧 Editing](#6-編輯技巧-editing)
7. [搜尋與取代 Search & Replace](#7-搜尋與取代-search--replace)
8. [快捷鍵 Keyboard Shortcuts](#8-快捷鍵-keyboard-shortcuts)
9. [擴充套件 Extensions](#9-擴充套件-extensions)
10. [終端機 Terminal](#10-終端機-terminal)
11. [Git 整合](#11-git-整合)
12. [多游標與選取技巧](#12-多游標與選取技巧)
13. [分割編輯器 Split Editor](#13-分割編輯器-split-editor)
14. [設定與個人化](#14-設定與個人化)
15. [Snippet 程式碼片段](#15-snippet-程式碼片段)
16. [AI 擴充套件整合](#16-ai-擴充套件整合)
17. [常見錯誤與注意事項](#17-常見錯誤與注意事項)
18. [速查表 Cheat Sheet](#18-速查表-cheat-sheet)

---

## 1. 什麼是 VS Code？

**Visual Studio Code**（簡稱 VS Code）是由 Microsoft 開發的免費開源程式編輯器，於 2015 年發布。儘管名稱含有「Visual Studio」，它與 Visual Studio IDE 是完全不同的產品。

```
VS Code 的本質：
一個可以無限擴充的純文字編輯器
+
輕量、快速、跨平台
+
龐大的擴充套件生態系
```

**VS Code 不是 IDE（整合開發環境）**，但透過擴充套件，它可以變得比 IDE 更強大。

### VS Code 的核心設計理念

- **輕量啟動** — 秒開，不像 IntelliJ 或 Eclipse 需要等待
- **語言無關** — 從 Python、JavaScript 到 Markdown、JSON 全部支援
- **擴充優先** — 核心保持精簡，功能透過套件擴充
- **開放原始碼** — 社群活躍，更新頻繁（每月發布新版）

---

## 2. 為什麼選擇 VS Code？

### VS Code vs. 其他編輯器

| 功能 | VS Code | Notepad++ | Sublime Text | IntelliJ |
|------|:-------:|:---------:|:------------:|:--------:|
| 免費 | ✅ | ✅ | ⚠️ 試用 | ⚠️ 付費 |
| 跨平台 | ✅ | ❌ Windows | ✅ | ✅ |
| AI 整合 | ✅ 原生 | ❌ | ❌ | ✅ |
| Git 整合 | ✅ 內建 | ❌ | 需套件 | ✅ |
| 擴充套件數量 | 5 萬+ | 少 | 中 | 中 |
| 啟動速度 | 快 | 極快 | 快 | 慢 |
| Markdown 預覽 | ✅ 內建 | 需套件 | 需套件 | 需套件 |

### 最適合 VS Code 的場景

- 撰寫 Markdown 文件（搭配 Marp 做簡報）
- 管理設定檔（JSON、YAML、TOML）
- 撰寫與執行程式碼（Python、JS 等）
- 使用 AI 輔助（GitHub Copilot、Claude）
- 管理 Git 版本控制

---

## 3. 安裝與初始設定

### 下載安裝

前往官網下載對應平台版本：`https://code.visualstudio.com`

| 平台 | 建議版本 |
|------|---------|
| Windows | User Installer（64-bit）|
| macOS | Universal（Intel + Apple Silicon）|
| Linux | .deb（Ubuntu）/ .rpm（Fedora）|

### 首次啟動設定清單

```
□ 選擇顯示語言（安裝中文語言包）
□ 選擇色彩主題（深色 / 淺色）
□ 登入 GitHub 帳號（同步設定）
□ 安裝必要擴充套件
□ 設定字型大小
```

### 安裝繁體中文介面

1. 按 `Ctrl+Shift+X` 開啟擴充套件
2. 搜尋 `Chinese (Traditional)`
3. 安裝 **Chinese (Traditional) Language Pack for VS Code**
4. 重新啟動 VS Code

---

## 4. 介面全覽

```
┌─────────────────────────────────────────────────────┐
│  標題列（Title Bar）                                  │
├──┬──────────────────────────────────────────────────┤
│  │  編輯器標籤列（Tabs）                              │
│活│──────────────────────────────────────────────────│
│動│                                                  │
│列│  編輯區（Editor Area）                            │
│  │                                                  │
│  │                                                  │
│  ├──────────────────────────────────────────────────│
│  │  終端機面板（Terminal Panel）                      │
├──┴──────────────────────────────────────────────────┤
│  狀態列（Status Bar）                                 │
└─────────────────────────────────────────────────────┘
```

### 活動列（Activity Bar）圖示說明

| 圖示 | 功能 | 快捷鍵 |
|------|------|--------|
| 檔案圖示 | 檔案總管 | `Ctrl+Shift+E` |
| 放大鏡 | 搜尋 | `Ctrl+Shift+F` |
| 分支圖示 | 原始碼控制（Git） | `Ctrl+Shift+G` |
| 三角形 | 執行與除錯 | `Ctrl+Shift+D` |
| 積木圖示 | 擴充套件 | `Ctrl+Shift+X` |

### 狀態列（Status Bar）資訊

```
[分支名稱] [錯誤數] [警告數]    [語言] [縮排] [編碼] [行尾]
    Git               問題         右側顯示目前檔案資訊
```

---

## 5. 檔案與資料夾管理

### 開啟資料夾（重要！）

VS Code 以**資料夾**為工作單位，建議開啟整個專案資料夾：

```
檔案 → 開啟資料夾   （Ctrl+K, Ctrl+O）
或直接將資料夾拖曳至 VS Code 視窗
```

### 檔案總管操作

| 操作 | 方法 |
|------|------|
| 新增檔案 | 點擊資料夾旁的「新增檔案」圖示，或右鍵 → 新增檔案 |
| 新增資料夾 | 點擊「新增資料夾」圖示 |
| 重新命名 | 點選檔案後按 `F2` |
| 刪除 | 右鍵 → 刪除，或選取後按 `Delete` |
| 移動 | 直接拖曳 |
| 複製路徑 | 右鍵 → 複製路徑 / 複製相對路徑 |

### 快速開啟檔案

```
Ctrl+P    → 輸入檔名快速跳轉（模糊搜尋）
Ctrl+Tab  → 在已開啟的標籤間切換
Ctrl+W    → 關閉目前標籤
```

### 工作區（Workspace）

將多個不相關的資料夾加入同一個工作區：

```
檔案 → 將資料夾新增至工作區
檔案 → 另存工作區...（儲存為 .code-workspace 檔）
```

---

## 6. 編輯技巧 Editing

### 基本編輯

| 操作 | 快捷鍵 |
|------|--------|
| 剪下整行 | `Ctrl+X`（游標在行內，不需選取） |
| 複製整行 | `Ctrl+C`（同上） |
| 刪除整行 | `Ctrl+Shift+K` |
| 向上/下移動整行 | `Alt+↑` / `Alt+↓` |
| 向上/下複製整行 | `Shift+Alt+↑` / `Shift+Alt+↓` |
| 縮排 / 取消縮排 | `Tab` / `Shift+Tab` |
| 切換行註解 | `Ctrl+/` |
| 切換區塊註解 | `Shift+Alt+A` |

### 游標移動

| 操作 | 快捷鍵 |
|------|--------|
| 跳至行首/行尾 | `Home` / `End` |
| 跳至檔案開頭/結尾 | `Ctrl+Home` / `Ctrl+End` |
| 跳至下一個單字 | `Ctrl+→` |
| 跳至特定行號 | `Ctrl+G` |
| 跳至匹配括號 | `Ctrl+Shift+\` |

### 選取技巧

| 操作 | 快捷鍵 |
|------|--------|
| 選取整行 | `Ctrl+L` |
| 展開選取範圍 | `Shift+Alt+→` |
| 縮小選取範圍 | `Shift+Alt+←` |
| 選取所有相同文字 | `Ctrl+Shift+L` |
| 選取下一個相同文字 | `Ctrl+D` |

### 自動格式化

```
Shift+Alt+F       → 格式化整份文件
Ctrl+K, Ctrl+F    → 格式化選取範圍
（右鍵 → 格式化文件）
```

---

## 7. 搜尋與取代 Search & Replace

### 單一檔案搜尋

```
Ctrl+F          開啟搜尋列
Enter           下一個結果
Shift+Enter     上一個結果
Alt+Enter       選取所有結果
Escape          關閉搜尋列
```

**搜尋選項圖示（搜尋列右側）：**

| 圖示 | 功能 | 快捷鍵 |
|------|------|--------|
| `Aa` | 區分大小寫 | `Alt+C` |
| `ab` | 全字比對 | `Alt+W` |
| `.*` | 正規表達式 | `Alt+R` |

### 全域搜尋（跨所有檔案）

```
Ctrl+Shift+F    開啟全域搜尋
```

**進階過濾：**
```
搜尋欄下方「要包含的檔案」：*.md, *.py
「要排除的檔案」：node_modules, *.min.js
```

### 取代

```
Ctrl+H          開啟取代（單一檔案）
Ctrl+Shift+H    開啟取代（全域）

取代欄位旁的圖示：
「取代」→ 取代目前項目
「全部取代」→ 取代所有結果
```

### 正規表達式搜尋範例

```regex
\d{4}-\d{2}-\d{2}     搜尋日期格式（2026-06-25）
https?://\S+           搜尋網址
^\s*$                  搜尋空白行
```

---

## 8. 快捷鍵 Keyboard Shortcuts

### 最重要的快捷鍵

```
Ctrl+Shift+P    命令面板（Command Palette）← 最重要！
Ctrl+P          快速開啟檔案
Ctrl+`          開啟/關閉終端機
Ctrl+B          開啟/關閉側邊欄
Ctrl+Z          復原
Ctrl+Shift+Z    取消復原
```

### 命令面板（Command Palette）

按 `Ctrl+Shift+P` 後輸入任何功能名稱，VS Code 會模糊搜尋所有可用命令：

```
> format document      格式化文件
> toggle word wrap     切換自動換行
> change language      切換程式語言
> install extension    安裝擴充套件
> open settings        開啟設定
> git commit           Git 提交
```

> **技巧：** 不記得快捷鍵？直接按 `Ctrl+Shift+P` 輸入功能名稱就好。

### 完整快捷鍵參考卡

```
Ctrl+K, Ctrl+S    → 開啟鍵盤快捷鍵設定頁面
```

### 自訂快捷鍵

```
Ctrl+Shift+P → "Open Keyboard Shortcuts (JSON)"
```

```json
[
  {
    "key": "ctrl+alt+t",
    "command": "workbench.action.terminal.new"
  }
]
```

---

## 9. 擴充套件 Extensions

### 安裝方式

1. `Ctrl+Shift+X` 開啟擴充套件面板
2. 搜尋套件名稱
3. 點擊「安裝」
4. 部分套件需重新載入視窗（`Ctrl+Shift+P` → "Reload Window"）

### 辦公室工作者必裝套件

| 套件名稱 | 功能 | 推薦指數 |
|---------|------|:-------:|
| **Marp for VS Code** | Markdown 簡報 | ⭐⭐⭐⭐⭐ |
| **Markdown All in One** | Markdown 增強（目錄、快捷鍵） | ⭐⭐⭐⭐⭐ |
| **Prettier** | 自動格式化 | ⭐⭐⭐⭐⭐ |
| **GitLens** | Git 視覺化增強 | ⭐⭐⭐⭐⭐ |
| **GitHub Copilot** | AI 程式碼補全 | ⭐⭐⭐⭐⭐ |
| **Chinese (Traditional)** | 繁體中文介面 | ⭐⭐⭐⭐⭐ |
| **Rainbow CSV** | CSV 彩色顯示 | ⭐⭐⭐⭐ |
| **Excel Viewer** | 在 VS Code 預覽 CSV/Excel | ⭐⭐⭐⭐ |
| **indent-rainbow** | 縮排彩色顯示 | ⭐⭐⭐⭐ |
| **Error Lens** | 將錯誤直接顯示在程式碼行 | ⭐⭐⭐⭐ |
| **Auto Rename Tag** | 自動更新 HTML 標籤 | ⭐⭐⭐⭐ |
| **Path Intellisense** | 路徑自動補全 | ⭐⭐⭐ |

### 程式開發套件（依語言）

| 語言 | 推薦套件 |
|------|---------|
| Python | Python（微軟官方）、Pylance |
| JavaScript/TypeScript | ESLint、Prettier |
| HTML/CSS | Live Server、CSS Peek |
| JSON | JSON Tools、Prettify JSON |
| Docker | Docker（微軟官方）|

### 管理套件

```
Ctrl+Shift+X → 「已安裝」標籤 → 可停用或解除安裝
套件過多會影響啟動速度，定期清理不用的套件
```

---

## 10. 終端機 Terminal

### 開啟終端機

```
Ctrl+`              開啟/關閉整合終端機
Ctrl+Shift+`        新增終端機
```

### 終端機基本操作

| 操作 | 方法 |
|------|------|
| 新增終端機 | 點選 `+` 圖示或 `Ctrl+Shift+`` |
| 分割終端機 | 點選分割圖示 |
| 切換終端機 | 點選下拉選單 |
| 清除畫面 | 輸入 `clear`（Mac/Linux）/ `cls`（Windows）|
| 終止程式 | `Ctrl+C` |

### 設定預設 Shell

```
Ctrl+Shift+P → "Terminal: Select Default Profile"
可選擇：PowerShell、Command Prompt、Git Bash、WSL
```

### 在終端機執行程式

```bash
# Python
python script.py

# Node.js
node app.js

# Marp CLI
marp slides.md --pdf

# Git
git status
git add .
git commit -m "更新內容"
```

---

## 11. Git 整合

VS Code 內建強大的 Git 介面：

### 基本 Git 工作流程（圖形介面）

```
1. 側邊欄點擊「原始碼控制」圖示（Ctrl+Shift+G）
2. 在「變更」區看到修改的檔案
3. 點擊檔案旁的「+」暫存（Stage）
4. 在訊息欄輸入 Commit 訊息
5. 按 Ctrl+Enter 或點擊「✓」提交（Commit）
6. 點擊「同步」推送到遠端
```

### 差異對比（Diff View）

點擊原始碼控制中的任一檔案，即可看到：
- **左側**：修改前
- **右側**：修改後
- 綠色：新增內容
- 紅色：刪除內容

### GitLens 擴充功能

安裝 GitLens 後，程式碼每行末尾會顯示：
```
let x = 5;    ← 你的名字，2 小時前：「修正計算邏輯」
```

---

## 12. 多游標與選取技巧

這是 VS Code 最省時的進階功能之一：

### 多游標（Multi-cursor）

```
Alt+點擊            在點擊處新增游標
Ctrl+Alt+↑/↓       在上/下行新增游標
Ctrl+D              選取下一個相同文字（可連按多次）
Ctrl+Shift+L        選取所有相同文字
Escape              回到單一游標
```

### 實際應用範例

**情境：要將 10 行清單的每行最前面加上 `-`**

1. 按 `Ctrl+Shift+P` → "Add Cursors to Line Ends" 或
2. 選取所有行 → `Shift+Alt+I`（在每行末尾加游標）

**情境：同時修改多處相同變數名稱**

1. 點選變數
2. 按 `Ctrl+Shift+L` 選取所有相同文字
3. 直接輸入新名稱

---

## 13. 分割編輯器 Split Editor

同時看兩份（或更多）檔案：

### 開啟分割

```
Ctrl+\              垂直分割（左右並排）
Ctrl+K, Ctrl+\      水平分割（上下並排）
拖曳標籤頁到邊緣     拖曳分割
```

### 實用場景

| 場景 | 左側 | 右側 |
|------|------|------|
| 對照翻譯 | 英文原文 | 中文翻譯 |
| Markdown 預覽 | 原始碼 | 渲染預覽 |
| 參考文件 | 文件 | 目前工作檔 |
| 程式比對 | 舊版程式 | 新版程式 |

### Markdown 並排預覽

```
開啟 .md 檔 → Ctrl+Shift+V    → 預覽頁面
                或點擊右上角預覽圖示（方形加放大鏡）
```

---

## 14. 設定與個人化

### 開啟設定

```
Ctrl+,              開啟設定（圖形介面）
Ctrl+Shift+P → "Open User Settings (JSON)"  → JSON 格式
```

### 常用設定項目

```json
{
  "editor.fontSize": 16,
  "editor.fontFamily": "Cascadia Code, Consolas, 微軟正黑體",
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "editor.minimap.enabled": false,
  "editor.renderWhitespace": "boundary",
  "editor.formatOnSave": true,
  "editor.lineHeight": 1.6,
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "terminal.integrated.fontSize": 14
}
```

### 推薦色彩主題

| 主題 | 風格 | 套件名稱 |
|------|------|---------|
| One Dark Pro | 深色、流行 | One Dark Pro |
| Dracula | 紫色系深色 | Dracula Official |
| GitHub Light | 淡色、清晰 | GitHub Theme |
| Tokyo Night | 深藍紫色 | Tokyo Night |
| Catppuccin | 柔和色系 | Catppuccin |

### 設定同步

登入 GitHub 或 Microsoft 帳號後，設定自動同步到所有裝置：

```
Ctrl+Shift+P → "Settings Sync: Turn On..."
```

---

## 15. Snippet 程式碼片段

Snippet 是可重複使用的程式碼範本，輸入縮寫後按 `Tab` 展開：

### 使用內建 Snippet

在 Markdown 檔案輸入：
```
table    → 按 Tab → 展開表格範本
link     → 按 Tab → 展開連結語法
```

### 建立自訂 Snippet

`Ctrl+Shift+P` → "Configure Snippets" → 選擇語言

```json
{
  "每日報告範本": {
    "prefix": "daily",
    "body": [
      "# 每日報告 — ${CURRENT_YEAR}-${CURRENT_MONTH}-${CURRENT_DATE}",
      "",
      "## 今日完成",
      "- $1",
      "",
      "## 明日計畫",
      "- $2",
      "",
      "## 問題與阻礙",
      "- $3"
    ],
    "description": "每日工作報告範本"
  }
}
```

### Snippet 變數

| 變數 | 說明 |
|------|------|
| `$1, $2, $3` | 游標停駐點，按 Tab 跳轉 |
| `$0` | 最終游標位置 |
| `${1:預設文字}` | 有預設值的停駐點 |
| `CURRENT_YEAR` | 當前年份 |
| `CURRENT_MONTH` | 當前月份 |
| `CURRENT_DATE` | 當前日期 |
| `TM_FILENAME` | 目前檔案名稱 |
| `CLIPBOARD` | 剪貼簿內容 |

---

## 16. AI 擴充套件整合

### GitHub Copilot

```
安裝套件：GitHub Copilot + GitHub Copilot Chat
需要：GitHub 帳號（教育版免費、付費方案 $10/月）
```

**使用方式：**
- 在程式碼中輸入註解，Copilot 會自動建議完整程式碼
- 按 `Tab` 接受建議，`Esc` 拒絕
- `Ctrl+I` 開啟行內 AI 對話

### Claude (Anthropic) 整合

```
安裝套件：Claude Dev 或 Continue
或使用 API 搭配自訂設定
```

### Codeium（免費 AI 補全）

```
安裝套件：Codeium
需要：免費帳號（無使用量限制）
```

### AI 工作流程建議

```
1. Claude.ai / ChatGPT 生成初稿
      ↓
2. 複製到 VS Code 編輯
      ↓
3. GitHub Copilot 協助細節補全
      ↓
4. 格式化與儲存
      ↓
5. Git 提交版本
```

---

## 17. 常見錯誤與注意事項

### ❌ 常見錯誤

**1. 直接開檔而非開資料夾**
```
❌ 檔案 → 開啟檔案（單一檔案模式，功能受限）
✅ 檔案 → 開啟資料夾（完整功能，Git 整合才能運作）
```

**2. 忘記儲存**
```
❌ 編輯後直接關視窗
✅ 設定 "files.autoSave": "afterDelay" 開啟自動儲存
   或記得按 Ctrl+S
```

**3. 修改了不該修改的設定**
```
Ctrl+Shift+P → "Open User Settings (JSON)"
→ 確認修改的是使用者設定，而非工作區設定
```

**4. 終端機路徑不對**
```
❌ 終端機停在其他目錄執行指令
✅ 確認終端機路徑與專案一致（看終端機的提示符號）
   或在檔案總管的資料夾上右鍵 → 「在整合終端機中開啟」
```

### ⚠️ 注意事項

- **擴充套件數量** — 太多會拖慢啟動速度，保持 10-15 個常用套件即可
- **設定同步** — 在不同電腦間同步設定前，確認帳號已登入
- **中文輸入法** — 部分快捷鍵與中文輸入法衝突，可在設定中調整
- **自動更新** — VS Code 會自動更新，介面偶爾有變化

### 💡 最佳實踐

1. **以資料夾為單位工作**，不要散開單獨開檔
2. **善用命令面板** `Ctrl+Shift+P`，任何功能都能在此找到
3. **定期清理不用的擴充套件**，保持輕量
4. **開啟自動儲存**，避免遺失工作
5. **學會多游標操作**，大幅提升編輯效率

---

## 18. 速查表 Cheat Sheet

```
## 介面控制
Ctrl+Shift+P    命令面板（最重要）
Ctrl+P          快速開啟檔案
Ctrl+B          切換側邊欄
Ctrl+`          切換終端機
Ctrl+,          開啟設定
Ctrl+K, Z       禪模式（全螢幕專注）

## 檔案操作
Ctrl+N          新增檔案
Ctrl+O          開啟檔案
Ctrl+S          儲存
Ctrl+Shift+S    另存新檔
Ctrl+W          關閉標籤
Ctrl+Shift+T    重新開啟已關閉標籤

## 編輯
Ctrl+Z / Y      復原 / 取消復原
Ctrl+X/C/V      剪下 / 複製 / 貼上
Ctrl+D          選取下一個相同文字
Ctrl+Shift+L    選取所有相同文字
Alt+↑/↓         移動整行
Shift+Alt+↑/↓   複製整行
Ctrl+Shift+K    刪除整行
Ctrl+/          切換註解
Shift+Alt+F     格式化文件

## 搜尋
Ctrl+F          搜尋（目前檔案）
Ctrl+H          取代（目前檔案）
Ctrl+Shift+F    全域搜尋
Ctrl+G          跳至行號

## 分割與導覽
Ctrl+\          分割編輯器
Ctrl+1/2/3      切換分割視窗
Ctrl+Tab        切換標籤
F12             跳至定義
Alt+←/→         導覽歷史
```

---

## 延伸學習資源

- [VS Code 官方文件](https://code.visualstudio.com/docs) — 完整功能說明
- [VS Code 快捷鍵參考（Windows）](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) — 官方 PDF
- [VS Code 快捷鍵參考（macOS）](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf) — 官方 PDF
- [VS Code YouTube 頻道](https://www.youtube.com/@code) — 官方影片教學
- [Anthropic Academy](https://www.anthropic.com/academy) — AI 工具整合學習

---

*本教材為「好好用 AI」課程補充教材 | CC BY-SA 4.0 | 2026*
