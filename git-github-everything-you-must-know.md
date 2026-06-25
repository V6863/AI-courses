# Everything You Must Know About Git & GitHub
### Git 與 GitHub 完全指南 — 好好用 AI 補充教材

> **適用對象：** 辦公室工作者、文件撰寫者、團隊協作者  
> **學習目標：** 用 Git 管理任何文字內容的版本，用 GitHub 進行團隊協作與分享

---

## 目錄

1. [什麼是 Git？什麼是 GitHub？](#1-什麼是-git什麼是-github)
2. [為什麼要學 Git？](#2-為什麼要學-git)
3. [安裝與初始設定](#3-安裝與初始設定)
4. [核心概念](#4-核心概念)
5. [基本工作流程](#5-基本工作流程)
6. [常用指令](#6-常用指令)
7. [分支 Branch](#7-分支-branch)
8. [遠端協作 Remote](#8-遠端協作-remote)
9. [GitHub 平台功能](#9-github-平台功能)
10. [Pull Request 協作流程](#10-pull-request-協作流程)
11. [GitHub Issues 任務管理](#11-github-issues-任務管理)
12. [.gitignore — 排除不需追蹤的檔案](#12-gitignore--排除不需追蹤的檔案)
13. [還原與修復](#13-還原與修復)
14. [VS Code 中使用 Git](#14-vs-code-中使用-git)
15. [Git 與 AI 工具的結合](#15-git-與-ai-工具的結合)
16. [常見錯誤與注意事項](#16-常見錯誤與注意事項)
17. [速查表 Cheat Sheet](#17-速查表-cheat-sheet)

---

## 1. 什麼是 Git？什麼是 GitHub？

### Git — 版本控制系統

**Git** 是一套在你電腦本機執行的版本控制工具，由 Linux 核心創始人 Linus Torvalds 於 2005 年開發。

```
沒有 Git：
report_final.docx
report_final_v2.docx
report_final_v2_真的最終版.docx
report_final_v2_真的最終版_改過.docx   ← 你有多少這種檔案？

有了 Git：
report.md（只有一個檔案）
    └── Git 幫你記錄每一次的修改歷史
```

### GitHub — 遠端平台

**GitHub** 是一個雲端服務平台，讓你把 Git 儲存庫放到網路上，實現：
- 備份與分享
- 多人協作
- 開放原始碼

### 關係圖

```
你的電腦
┌─────────────────────────────┐
│  工作目錄（Working Directory）│
│       ↕ git add             │
│  暫存區（Staging Area）       │
│       ↕ git commit          │
│  本地儲存庫（Local Repo）     │
└────────────┬────────────────┘
             │ git push / git pull
             ↕
┌────────────────────────────┐
│  GitHub（遠端儲存庫）        │
│  其他協作者也可以存取         │
└────────────────────────────┘
```

### Git vs. GitHub vs. 其他平台

| | Git | GitHub | GitLab | Bitbucket |
|--|:---:|:------:|:------:|:---------:|
| 本機工具 | ✅ | ❌ | ❌ | ❌ |
| 雲端平台 | ❌ | ✅ | ✅ | ✅ |
| 免費私有儲存庫 | — | ✅ | ✅ | ✅ |
| CI/CD | — | ✅ Actions | ✅ | ✅ |
| 最大社群 | — | ✅ | — | — |

---

## 2. 為什麼要學 Git？

### 不只是給工程師的工具

| 使用情境 | 說明 |
|---------|------|
| **文件版本管理** | Markdown 報告、簡報、文案的修改歷史 |
| **AI 提示詞管理** | 儲存並追蹤你精心設計的 Prompt |
| **團隊協作** | 多人同時編輯，不怕覆蓋彼此的工作 |
| **備份** | Push 到 GitHub = 雲端備份 |
| **回溯任何版本** | 隨時回到任何一個過去的狀態 |
| **比對差異** | 清楚看到「改了什麼」 |

### Git 解決的核心問題

```
問題一：「我不記得上週改了什麼」
→ git log 查看完整修改歷史

問題二：「改壞了，想回到之前的版本」
→ git revert 或 git checkout 回復舊版

問題三：「兩個人同時改同一份文件，衝突了」
→ Git 的合併（merge）機制解決衝突

問題四：「想試試新方向，但不想影響正式版本」
→ git branch 開新分支實驗
```

---

## 3. 安裝與初始設定

### 安裝 Git

| 平台 | 方法 |
|------|------|
| **Windows** | 下載 Git for Windows（git-scm.com）|
| **macOS** | `brew install git` 或 Xcode Command Line Tools |
| **Linux** | `sudo apt install git`（Ubuntu）|

**確認安裝成功：**
```bash
git --version
# 輸出：git version 2.x.x
```

### 第一次使用：設定身份

這是**必做步驟**，每次 commit 都會記錄這些資訊：

```bash
git config --global user.name "你的名字"
git config --global user.email "your@email.com"
```

### 其他推薦設定

```bash
# 設定預設編輯器為 VS Code
git config --global core.editor "code --wait"

# 設定預設分支名稱為 main（新版 Git 標準）
git config --global init.defaultBranch main

# 查看目前所有設定
git config --list
```

### 安裝 GitHub Desktop（圖形介面，新手推薦）

下載 GitHub Desktop，提供視覺化介面，不需記指令：
`https://desktop.github.com`

---

## 4. 核心概念

### 四個狀態

```
┌─────────────────────────────────────────────────────┐
│  未追蹤（Untracked）                                  │
│  新建立的檔案，Git 還不知道它的存在                     │
│                     ↓ git add                        │
│  已暫存（Staged）                                     │
│  已加入暫存區，準備被 commit                           │
│                     ↓ git commit                     │
│  已提交（Committed）                                  │
│  已記錄到本地儲存庫                                    │
│                     ↓ 修改檔案                        │
│  已修改（Modified）                                   │
│  已被追蹤的檔案有了變動，等待 add 再 commit             │
└─────────────────────────────────────────────────────┘
```

### Commit — 版本快照

每個 Commit 就像一張「存檔」：

```
commit a3f9c2d
Author: 你的名字 <email>
Date:   2026-06-25 14:30:00

    新增 Q2 市場分析報告
```

**好的 Commit 訊息格式：**
```
<類型>: <簡短說明>（50字以內）

<詳細說明>（可選）
```

| 類型 | 用途 |
|------|------|
| `feat` | 新增功能或內容 |
| `fix` | 修正錯誤 |
| `docs` | 文件修改 |
| `style` | 格式調整（不影響內容） |
| `refactor` | 重構（不新增也不修復） |
| `update` | 更新既有內容 |

### Repository（儲存庫）

一個 Repository（Repo）= 一個受 Git 管理的資料夾：

```
my-project/
├── .git/            ← Git 的資料夾（不要手動修改）
├── README.md
├── docs/
│   ├── report.md
│   └── slides.md
└── assets/
    └── logo.png
```

---

## 5. 基本工作流程

### 新專案的完整流程

```bash
# 1. 建立資料夾並進入
mkdir my-project
cd my-project

# 2. 初始化 Git
git init

# 3. 建立第一個檔案
echo "# My Project" > README.md

# 4. 加入暫存區
git add README.md

# 5. 提交
git commit -m "docs: 新增 README"

# 6. 連接 GitHub 遠端（建立遠端 repo 後）
git remote add origin https://github.com/你的帳號/my-project.git

# 7. 推送到 GitHub
git push -u origin main
```

### 日常修改流程

```bash
# 查看目前狀態
git status

# 查看哪些地方被修改了
git diff

# 加入所有修改
git add .

# 或加入特定檔案
git add report.md slides.md

# 提交
git commit -m "update: 更新 Q2 報告數據"

# 推送
git push
```

### 狀態查看的解讀

```bash
$ git status

On branch main
Changes to be committed:    ← 已暫存，準備 commit
  (use "git restore --staged <file>..." to unstage)
        modified:   report.md

Changes not staged for commit:  ← 已修改但未暫存
  (use "git add <file>..." to update what will be committed)
        modified:   slides.md

Untracked files:              ← 新檔案，未追蹤
  (use "git add <file>..." to include in what will be committed)
        new-draft.md
```

---

## 6. 常用指令

### 初始化與設定

```bash
git init                          建立新的 Git 儲存庫
git clone <URL>                   複製遠端儲存庫到本機
git config --global user.name ""  設定使用者名稱
git config --global user.email "" 設定 Email
```

### 狀態與歷史

```bash
git status                  查看目前狀態
git log                     查看完整 commit 歷史
git log --oneline           一行顯示 commit 歷史
git log --oneline --graph   圖形化顯示分支歷史
git diff                    查看未暫存的修改
git diff --staged           查看已暫存的修改
git show <commit>           查看某次 commit 的詳細內容
```

### 新增與提交

```bash
git add <檔案>              加入特定檔案到暫存區
git add .                   加入所有修改到暫存區
git add -p                  互動式逐塊選擇要暫存的內容
git commit -m "訊息"        提交（帶訊息）
git commit -am "訊息"       合併 add 和 commit（僅限已追蹤檔案）
git commit --amend          修改最後一次 commit（未 push 才能用）
```

### 遠端操作

```bash
git remote add origin <URL> 設定遠端儲存庫
git remote -v               查看遠端設定
git push                    推送到遠端
git push -u origin main     首次推送並設定追蹤
git pull                    拉取並合併遠端更新
git fetch                   拉取遠端更新（不合併）
```

### 常用組合

```bash
# 查看一行歷史
git log --oneline -10

# 推送並追蹤遠端分支
git push -u origin main

# 拉取最新變更
git pull origin main
```

---

## 7. 分支 Branch

### 什麼是分支？

```
main ─────●─────●─────●─────●──→  正式版本
               │               ↑
               └───●─────●────┘   feature/new-report
                   開新分支實驗    完成後合併回 main
```

### 分支操作

```bash
git branch                    查看所有分支
git branch feature/new-report 建立新分支
git switch feature/new-report 切換到新分支
git switch -c feature/draft   建立並立即切換（合併上面兩行）
git branch -d feature/done    刪除已合併的分支
git branch -D feature/abort   強制刪除分支
```

### 合併分支

```bash
# 切換回主分支
git switch main

# 合併 feature 分支
git merge feature/new-report

# 合併後刪除 feature 分支
git branch -d feature/new-report
```

### 解決合併衝突

當兩個分支都修改了同一個地方，Git 會標示衝突：

```
<<<<<<< HEAD（目前分支）
這是 main 分支的內容
=======
這是 feature 分支的內容
>>>>>>> feature/new-report
```

**解決方法：**
1. 開啟衝突的檔案
2. 手動選擇要保留哪個版本（或結合兩者）
3. 刪除 `<<<<<<<`、`=======`、`>>>>>>>` 標記
4. `git add <檔案>` → `git commit`

**VS Code 提供視覺化衝突解決介面，強烈推薦使用。**

---

## 8. 遠端協作 Remote

### 克隆（Clone）現有專案

```bash
git clone https://github.com/帳號/專案名稱.git
cd 專案名稱
```

### 同步遠端更新

```bash
# 每次開始工作前先拉取最新版本
git pull

# 完成後推送
git push
```

### 多人協作標準流程

```bash
# 1. 每天開始工作：拉取最新版本
git pull origin main

# 2. 建立功能分支
git switch -c feature/我的修改

# 3. 修改、新增檔案
# ... 編輯檔案 ...

# 4. 提交
git add .
git commit -m "feat: 新增市場分析章節"

# 5. 推送分支到遠端
git push -u origin feature/我的修改

# 6. 在 GitHub 上發起 Pull Request
# 7. 等待審核、合併
```

---

## 9. GitHub 平台功能

### 帳號設定

1. 前往 `https://github.com` 註冊帳號
2. 設定頭像與個人簡介
3. 在 Settings → SSH Keys 設定 SSH 金鑰（可選，讓 push 不需輸入密碼）

### 建立新儲存庫（Repository）

1. 點擊右上角 `+` → New repository
2. 填寫名稱、說明
3. 選擇 Public（公開）或 Private（私有）
4. 勾選「Add a README file」（建議）
5. 點擊 Create repository

### GitHub 介面說明

```
Repository 頁面：
├── Code          → 瀏覽檔案與 commit 歷史
├── Issues        → 任務與問題追蹤
├── Pull Requests → 程式碼審查與合併請求
├── Actions       → CI/CD 自動化流程
├── Projects      → 看板式任務管理
├── Wiki          → 文件說明
├── Settings      → 儲存庫設定、成員管理
└── Insights      → 貢獻統計
```

### 重要功能

| 功能 | 說明 |
|------|------|
| **Star** | 收藏感興趣的專案 |
| **Fork** | 複製別人的專案到自己帳號 |
| **Watch** | 訂閱專案更新通知 |
| **README.md** | 自動顯示在 repo 首頁 |
| **Releases** | 發布正式版本 |
| **GitHub Pages** | 免費靜態網站託管 |

---

## 10. Pull Request 協作流程

**Pull Request（PR）** 是 GitHub 上最重要的協作機制，讓他人審查你的修改後再合併。

### PR 完整流程

```
1. Fork 或 Clone 專案
       ↓
2. 建立功能分支
   git switch -c feature/我的修改
       ↓
3. 修改並提交
   git add . && git commit -m "..."
       ↓
4. 推送分支
   git push -u origin feature/我的修改
       ↓
5. 在 GitHub 建立 Pull Request
   → 填寫標題與說明
   → 指定 Reviewer（審查者）
       ↓
6. 討論與修改
   → Reviewer 留下評論
   → 作者根據回饋修改並 push
       ↓
7. 批准（Approve）與合併（Merge）
       ↓
8. 刪除已合併的分支
```

### 好的 PR 說明範本

```markdown
## 這個 PR 做了什麼？
- 新增 Q2 市場分析章節
- 更新競品比較表格
- 修正第 3 頁的錯字

## 為什麼這樣做？
根據行銷會議（2026-06-20）的回饋，需要加強競品分析部分。

## 如何測試？
- [ ] 開啟文件確認排版正常
- [ ] 確認所有連結有效
- [ ] 確認數據與原始資料一致

## 截圖（如適用）
[貼上截圖]
```

---

## 11. GitHub Issues 任務管理

**Issues** 是 GitHub 上追蹤任務、回報問題的功能：

### 建立 Issue

1. 進入 Repository → Issues → New issue
2. 填寫標題（具體描述問題或任務）
3. 在說明欄填寫詳細內容
4. 設定 Label（標籤）、Assignee（負責人）、Milestone

### 常用 Label 設定

| Label | 含義 |
|-------|------|
| `bug` | 問題回報 |
| `enhancement` | 功能改善 |
| `documentation` | 文件相關 |
| `question` | 疑問討論 |
| `help wanted` | 需要協助 |
| `priority: high` | 高優先順序 |

### 在 Commit 訊息中關聯 Issue

```bash
git commit -m "fix: 修正報告日期格式 #12"
# #12 會自動連結到 Issue #12

git commit -m "fix: 修正報告日期格式 closes #12"
# PR 合併後自動關閉 Issue #12
```

### Markdown 在 Issues 中的應用

```markdown
## 問題描述
報告第 5 頁的圖表數據與 Excel 原始檔不符。

## 重現步驟
1. 開啟 `Q2_report.md`
2. 查看第 5 頁「成長率」圖表
3. 對比 `data/Q2_raw.xlsx` 中 B 欄數據

## 期望結果
圖表數據應與 Excel 一致（成長率 23%）

## 目前結果
圖表顯示 18%（錯誤）

## 截圖
[貼上截圖]
```

---

## 12. .gitignore — 排除不需追蹤的檔案

`.gitignore` 告訴 Git 哪些檔案不要追蹤：

```bash
# 在專案根目錄建立 .gitignore 檔案
touch .gitignore
```

### .gitignore 語法

```gitignore
# 忽略特定檔案
secret.txt
passwords.json

# 忽略特定副檔名
*.log
*.tmp
*.bak

# 忽略整個資料夾
node_modules/
__pycache__/
.venv/

# 忽略特定資料夾下的某類型檔案
build/*.pdf

# 用 ! 取消忽略
*.pdf
!important.pdf    ← 這個 PDF 例外，要追蹤

# 忽略作業系統產生的檔案
.DS_Store          ← macOS
Thumbs.db          ← Windows
desktop.ini        ← Windows
```

### 辦公室工作常見的 .gitignore

```gitignore
# 個人設定
.env
*.local

# 作業系統
.DS_Store
Thumbs.db
desktop.ini

# 編輯器
.vscode/settings.json
*.swp
*~

# 暫存輸出
output/
dist/
*.pdf
*.pptx

# 機密檔案
secrets/
credentials.json
*_private.*
```

---

## 13. 還原與修復

### 情境一：修改了檔案但還沒 add，想還原

```bash
git restore <檔案>       還原單一檔案
git restore .            還原所有修改
```

### 情境二：已經 add 了，想取消暫存

```bash
git restore --staged <檔案>    取消暫存（保留修改）
```

### 情境三：想修改最後一次 commit（尚未 push）

```bash
# 只修改 commit 訊息
git commit --amend -m "新的訊息"

# 新增檔案到最後一次 commit
git add 忘記的檔案
git commit --amend --no-edit
```

### 情境四：想回到某個舊版本查看

```bash
git log --oneline           # 找到目標 commit 的 hash
git checkout abc1234        # 暫時切換到那個版本（只讀）
git switch main             # 回到目前版本
```

### 情境五：想完全回到舊版本（危險！）

```bash
# 安全的方式：建立新 commit 來反轉某次修改
git revert abc1234

# 危險的方式：捨棄之後所有 commit（確定才用）
git reset --hard abc1234
```

### 情境六：不小心 commit 了機密檔案

```bash
# 從追蹤中移除（保留檔案在本地）
git rm --cached secrets.json
echo "secrets.json" >> .gitignore
git commit -m "fix: 移除機密檔案追蹤"
git push
```

> **警告：** 如果已 push 到 GitHub，機密資料可能已被他人看到。請立即更換密碼/金鑰，並聯繫管理員。

---

## 14. VS Code 中使用 Git

### 圖形介面（不需記指令）

```
左側活動列 → 原始碼控制圖示（Ctrl+Shift+G）
```

| 操作 | VS Code 動作 |
|------|-------------|
| git status | 查看「變更」清單 |
| git add | 點擊檔案旁的「+」 |
| git commit | 輸入訊息後按 ✓ 或 Ctrl+Enter |
| git push | 點擊「同步變更」或「↑」 |
| git pull | 點擊「同步變更」或「↓」 |
| git diff | 點擊變更的檔案查看差異 |

### 實用 VS Code Git 擴充套件

| 套件 | 功能 |
|------|------|
| **GitLens** | 每行程式碼顯示最後修改者與時間 |
| **Git Graph** | 視覺化分支圖表 |
| **Git History** | 圖形化查看 commit 歷史 |

### 衝突解決介面

在 VS Code 中遇到衝突，會看到直覺的按鈕：

```
[Accept Current Change]    保留目前分支的版本
[Accept Incoming Change]   保留合併進來的版本
[Accept Both Changes]      保留兩者
[Compare Changes]          開啟比對視圖
```

---

## 15. Git 與 AI 工具的結合

### 用 AI 生成 Commit 訊息

把 `git diff --staged` 的輸出貼給 AI：

```markdown
以下是我的 git diff 輸出，請幫我寫一個清楚的 commit 訊息，
格式：<類型>: <簡短說明>（50字以內）

[貼上 git diff 輸出]
```

### 用 AI 協助解決衝突

把衝突內容貼給 AI：

```markdown
我在合併 Git 分支時遇到衝突，請幫我決定如何解決：

目前分支（main）的內容：
[貼上 <<<<<<< HEAD 到 ======= 之間的內容]

合併進來的分支內容：
[貼上 ======= 到 >>>>>>> 之間的內容]

這份文件的用途是：[說明文件用途]
請建議如何合併這兩個版本。
```

### 用 AI 管理 Prompt 版本

把你的 AI 提示詞也用 Git 管理：

```
prompts/
├── report-generator.md      生成報告的 prompt
├── email-writer.md          撰寫 Email 的 prompt
├── meeting-summary.md       會議摘要的 prompt
└── CHANGELOG.md             記錄 prompt 修改歷史
```

```bash
git commit -m "feat: 在報告 prompt 加入輸出格式要求，回應品質提升 40%"
```

### GitHub 作為 AI 輸出的版本倉庫

- 將 AI 生成的文件放入 Git 管理
- 每次重新生成時比對差異（`git diff`）
- 保留最佳版本的 Commit

---

## 16. 常見錯誤與注意事項

### ❌ 常見錯誤

**1. 忘記設定身份就 commit**
```bash
# 症狀：commit 顯示奇怪的 email
# 修復：
git config --global user.name "你的名字"
git config --global user.email "your@email.com"
```

**2. 直接在 main 分支工作**
```bash
# 習慣在新分支工作，main 保持乾淨
git switch -c feature/我的新工作
```

**3. commit 了機密資訊（密碼、金鑰）**
```bash
# 立即用 git rm --cached 移除並更換密碼
# 事先建立 .gitignore 避免此問題
```

**4. git pull 前沒有 commit**
```bash
# 症狀：error: Your local changes would be overwritten
# 修復：先 commit 或 stash
git stash          # 暫時儲存修改
git pull
git stash pop      # 取回修改
```

**5. Push 到了錯誤的分支**
```bash
# 確認目前分支
git branch

# 確認遠端設定
git remote -v
```

### ⚠️ 注意事項

- **不要刪除 `.git` 資料夾** — 那是 Git 的核心，刪除後版本歷史全部消失
- **`git reset --hard` 很危險** — 會永久刪除未提交的修改
- **公開 Repository 不要放機密** — GitHub 上的 Public repo 全世界都能看到
- **大檔案不適合 Git** — 圖片、影片、Excel 大檔案請用 Git LFS 或其他方案

### 💡 最佳實踐

1. **常 commit，小 commit** — 每完成一個小任務就 commit，不要積累太多再一次 commit
2. **commit 訊息要有意義** — 未來的你會感謝現在寫清楚訊息的你
3. **在新分支實驗** — 不確定的修改開新分支，確認後再合併
4. **每天 pull 一次** — 多人協作時，每天開始前先拉取最新版本
5. **Push 前先 Pull** — 避免推送衝突

---

## 17. 速查表 Cheat Sheet

```
## 初始設定
git config --global user.name "名字"
git config --global user.email "email"

## 建立與克隆
git init                     初始化新 repo
git clone <URL>              克隆遠端 repo

## 狀態與歷史
git status                   查看狀態
git log --oneline            查看 commit 歷史
git diff                     查看未暫存的修改
git diff --staged            查看已暫存的修改

## 新增與提交
git add <檔案>               暫存特定檔案
git add .                    暫存所有修改
git commit -m "訊息"         提交
git commit --amend           修改最後一次 commit

## 分支
git branch                   查看分支
git switch -c <分支名>       建立並切換分支
git switch <分支名>          切換分支
git merge <分支名>           合併分支
git branch -d <分支名>       刪除分支

## 遠端
git remote add origin <URL>  設定遠端
git push                     推送
git push -u origin main      首次推送
git pull                     拉取並合併
git fetch                    只拉取不合併

## 還原
git restore <檔案>           還原未暫存的修改
git restore --staged <檔案>  取消暫存
git revert <commit>          安全地回退某次 commit
git stash                    暫存目前修改
git stash pop                取回暫存的修改
```

---

## 延伸學習資源

- [Git 官方文件](https://git-scm.com/doc) — 完整參考手冊
- [Pro Git（免費電子書）](https://git-scm.com/book/zh-tw/v2) — 繁體中文版，深入完整
- [GitHub Skills](https://skills.github.com/) — GitHub 官方互動課程（免費）
- [Learn Git Branching](https://learngitbranching.js.org/?locale=zh_TW) — 視覺化學習分支概念
- [GitHub Docs](https://docs.github.com/) — GitHub 平台完整文件
- [Anthropic Academy](https://www.anthropic.com/academy) — AI 工具整合學習

---

*本教材為「好好用 AI」課程補充教材 | CC BY-SA 4.0 | 2026*
