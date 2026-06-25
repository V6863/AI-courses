# Everything You Must Know About Markdown
### Markdown 完全指南 — 好好用 AI 補充教材

> **適用對象：** 辦公室工作者、AI 工具使用者  
> **學習目標：** 掌握 Markdown 語法，讓你在 ChatGPT、Claude、Notion、GitHub 等工具中寫出結構清晰的內容

---

## 目錄

1. [什麼是 Markdown？](#1-什麼是-markdown)
2. [為什麼要學 Markdown？](#2-為什麼要學-markdown)
3. [標題 Headings](#3-標題-headings)
4. [段落與換行 Paragraphs & Line Breaks](#4-段落與換行)
5. [文字格式 Text Formatting](#5-文字格式-text-formatting)
6. [清單 Lists](#6-清單-lists)
7. [連結與圖片 Links & Images](#7-連結與圖片-links--images)
8. [引用區塊 Blockquotes](#8-引用區塊-blockquotes)
9. [程式碼 Code](#9-程式碼-code)
10. [表格 Tables](#10-表格-tables)
11. [分隔線 Horizontal Rules](#11-分隔線-horizontal-rules)
12. [進階語法 Extended Syntax](#12-進階語法-extended-syntax)
13. [Markdown 在 AI 工具中的應用](#13-markdown-在-ai-工具中的應用)
14. [常用工具與平台](#14-常用工具與平台)
15. [常見錯誤與注意事項](#15-常見錯誤與注意事項)
16. [速查表 Cheat Sheet](#16-速查表-cheat-sheet)

---

## 1. 什麼是 Markdown？

**Markdown** 是一種輕量級的標記語言（Markup Language），由 John Gruber 於 2004 年創立。它讓你用純文字（plain text）就能排版出有結構的文件，不需要 Word 或 HTML。

```
你寫的文字                →    轉換後的結果
# 大標題                  →    <h1>大標題</h1>
**粗體**                  →    <b>粗體</b>
- 項目                    →    • 項目
```

**核心哲學：** 即使不渲染，原始文字也要易於閱讀。

---

## 2. 為什麼要學 Markdown？

| 使用情境 | 說明 |
|---------|------|
| **AI 對話** | 在 Claude、ChatGPT 中用 Markdown 提問，輸出更有結構 |
| **Notion / Obsidian** | 主流筆記工具的核心語法 |
| **GitHub / GitLab** | README、Issue、PR 說明全靠 Markdown |
| **技術文件** | 幾乎所有開發者文件的標準格式 |
| **簡報輔助** | Marp、Slidev 可將 Markdown 轉成簡報 |
| **Email / 報告** | 結構化思考的輸出載體 |

---

## 3. 標題 Headings

用 `#` 符號表示標題，`#` 越多層級越低：

```markdown
# H1 — 最大標題（一份文件通常只用一個）
## H2 — 章節標題
### H3 — 小節標題
#### H4 — 子項標題
##### H5
###### H6 — 最小標題
```

**注意：** `#` 後面必須加一個空格。

---

## 4. 段落與換行

### 段落（Paragraph）

兩段文字之間**空一行**，就會產生新段落：

```markdown
這是第一段。
這行和上面在同一段。

這是第二段，因為上面有空行。
```

### 強制換行（Line Break）

行尾加**兩個空格**再按 Enter，或使用 `<br>`：

```markdown
第一行（行尾有兩個空格）  
第二行（會換行但不新增段落）
```

---

## 5. 文字格式 Text Formatting

| 效果 | 語法 | 範例 |
|------|------|------|
| **粗體** | `**文字**` 或 `__文字__` | `**重要**` → **重要** |
| *斜體* | `*文字*` 或 `_文字_` | `*強調*` → *強調* |
| ***粗斜體*** | `***文字***` | `***極重要***` → ***極重要*** |
| ~~刪除線~~ | `~~文字~~` | `~~舊版本~~` → ~~舊版本~~ |
| `行內程式碼` | `` `文字` `` | `` `print()` `` → `print()` |
| ==highlight== | `==文字==` | 部分平台支援（如 Obsidian） |

---

## 6. 清單 Lists

### 無序清單（Unordered List）

使用 `-`、`*` 或 `+`（建議統一用 `-`）：

```markdown
- 蘋果
- 香蕉
- 橘子
  - 血橙（縮排兩格變子項目）
  - 臍橙
```

**輸出：**
- 蘋果
- 香蕉
- 橘子
  - 血橙
  - 臍橙

### 有序清單（Ordered List）

```markdown
1. 第一步：開啟工具
2. 第二步：輸入提示詞
3. 第三步：確認輸出
```

> 小技巧：數字不一定要正確，Markdown 會自動排序。全部寫 `1.` 也沒關係。

### 任務清單（Task List）

```markdown
- [x] 完成 Markdown 教材
- [x] 審閱內容
- [ ] 發布到課程平台
- [ ] 收集學員回饋
```

**輸出（支援平台上會顯示勾選框）：**
- [x] 完成 Markdown 教材
- [x] 審閱內容
- [ ] 發布到課程平台
- [ ] 收集學員回饋

---

## 7. 連結與圖片 Links & Images

### 連結

```markdown
[顯示文字](URL)
[顯示文字](URL "滑鼠懸停提示文字")

範例：
[Anthropic Academy](https://www.anthropic.com/academy)
[Google](https://google.com "搜尋引擎")
```

**輸出：** [Anthropic Academy](https://www.anthropic.com/academy)

### 參考式連結（Reference Links）

適合在文章中多次引用同一連結：

```markdown
請參考 [Anthropic][1] 和 [Claude][2] 的官方文件。

[1]: https://www.anthropic.com
[2]: https://claude.ai
```

### 圖片

語法和連結相同，前面多一個 `!`：

```markdown
![替代文字](圖片URL)
![替代文字](圖片URL "圖片標題")

範例：
![公司 Logo](https://example.com/logo.png "Company Logo")
```

### 可點擊的圖片（連結包圖片）

```markdown
[![替代文字](圖片URL)](連結URL)
```

---

## 8. 引用區塊 Blockquotes

用 `>` 開頭：

```markdown
> 這是一段引用文字。
> 可以跨越多行。
>
> 甚至可以有多個段落。
```

**輸出：**
> 這是一段引用文字。
> 可以跨越多行。
>
> 甚至可以有多個段落。

### 巢狀引用

```markdown
> 外層引用
>
>> 內層引用（縮排一層）
```

### 引用內可以包含其他語法

```markdown
> #### 引用內的標題
>
> - 引用內的清單
> - 第二項
>
> **粗體**也可以用
```

---

## 9. 程式碼 Code

### 行內程式碼（Inline Code）

用反引號 `` ` `` 包住：

```markdown
使用 `Ctrl+C` 複製，`Ctrl+V` 貼上。
```

**輸出：** 使用 `Ctrl+C` 複製，`Ctrl+V` 貼上。

### 程式碼區塊（Code Block）

用三個反引號 ` ``` ` 包住，可指定語言以啟用語法高亮：

````markdown
```python
def hello():
    print("Hello, World!")
    return True
```

```javascript
const greet = (name) => {
  console.log(`Hello, ${name}!`);
};
```

```bash
cd ~/Documents
ls -la
git status
```
````

### 縮排式程式碼區塊

每行縮排 4 個空格也會變成程式碼區塊（較舊的寫法，不建議使用）：

```markdown
    這是程式碼
    第二行
```

---

## 10. 表格 Tables

```markdown
| 欄位一 | 欄位二 | 欄位三 |
|--------|--------|--------|
| 資料 A | 資料 B | 資料 C |
| 資料 D | 資料 E | 資料 F |
```

### 對齊方式

```markdown
| 靠左對齊 | 置中對齊 | 靠右對齊 |
|:---------|:--------:|---------:|
| 文字     |   文字   |     文字 |
| 123      |   456    |      789 |
```

**輸出：**

| 靠左對齊 | 置中對齊 | 靠右對齊 |
|:---------|:--------:|---------:|
| 文字     |   文字   |     文字 |
| 123      |   456    |      789 |

> **小技巧：** 欄位不需要對齊，只要 `|` 存在就行。用 [Markdown Table Generator](https://www.tablesgenerator.com/markdown_tables) 可以快速生成表格。

---

## 11. 分隔線 Horizontal Rules

三個以上的 `-`、`*` 或 `_`（單獨一行）：

```markdown
---

***

___
```

三種都會產生水平分隔線。

---

## 12. 進階語法 Extended Syntax

> 以下語法並非所有平台都支援，請依使用工具確認。

### 腳註（Footnotes）

```markdown
這是一段有腳註的文字[^1]，還有另一個[^注意]。

[^1]: 這是第一個腳註的內容。
[^注意]: 腳註可以用文字命名。
```

### 定義清單（Definition Lists）

```markdown
Markdown
:   一種輕量標記語言

HTML
:   超文字標記語言
:   用於網頁結構
```

### 數學公式（Math）

部分平台（Notion、Obsidian、GitHub）支援 LaTeX：

```markdown
行內公式：$E = mc^2$

獨立公式：
$$
\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n
$$
```

### Emoji

```markdown
:smile: :rocket: :white_check_mark:
```

或直接貼上 Emoji：🎉 ✅ 🚀

### HTML 嵌入

Markdown 允許直接嵌入 HTML：

```markdown
<details>
<summary>點擊展開</summary>

這裡是隱藏的內容。

</details>

<mark>螢光筆效果</mark>

文字<sup>上標</sup>與文字<sub>下標</sub>
```

---

## 13. Markdown 在 AI 工具中的應用

### 用 Markdown 寫出更好的 Prompt

結構化的提示詞讓 AI 更容易理解你的需求：

````markdown
# 任務
請幫我撰寫一份產品介紹

## 產品資訊
- **名稱：** 智慧會議助理
- **目標客群：** 中小企業主管
- **核心功能：** 自動錄音、逐字稿、行動項目摘要

## 輸出格式要求
1. 開場白（2 句話）
2. 三大亮點（條列式）
3. 呼籲行動（CTA）

## 語氣
專業但不失親切，避免過度技術性用語
````

### 讓 AI 輸出 Markdown 格式

在提示詞中明確要求：

```markdown
請用 Markdown 格式回答，包含：
- ## 標題 分隔各段落
- **粗體** 標示重點
- 表格 比較不同選項
- 程式碼區塊 呈現任何程式碼
```

### Markdown 在各 AI 工具的支援狀況

| 工具 | 渲染 Markdown | 接受 Markdown 輸入 |
|------|:------------:|:-----------------:|
| Claude.ai | ✅ | ✅ |
| ChatGPT | ✅ | ✅ |
| Gemini | ✅ | ✅ |
| Copilot | ✅ | ✅ |

---

## 14. 常用工具與平台

### 編輯器

| 工具 | 特色 | 適合對象 |
|------|------|---------|
| **Obsidian** | 本地筆記、雙向連結 | 知識管理 |
| **Notion** | 線上協作、資料庫 | 團隊協作 |
| **VS Code** | 程式開發、預覽插件 | 開發者 |
| **Typora** | 即時渲染、所見即所得 | 文件寫作 |
| **HackMD** | 線上協作 Markdown | 快速分享 |
| **Zettlr** | 學術寫作 | 研究人員 |

### 線上工具

- **Markdown Live Preview** — 即時預覽
- **Dillinger** — 線上編輯器（dillinger.io）
- **Tables Generator** — 快速生成表格
- **Markdown to PDF** — 格式轉換

### 轉換工具

```
Markdown → PDF       Pandoc、Typora 匯出
Markdown → Word      Pandoc
Markdown → 簡報      Marp、Slidev、Reveal.js
Markdown → 網站      Hugo、Jekyll、MkDocs
```

---

## 15. 常見錯誤與注意事項

### ❌ 常見錯誤

**1. `#` 後面沒有空格**
```markdown
#標題（錯誤）
# 標題（正確）
```

**2. 清單項目前沒有空格**
```markdown
-項目（錯誤）
- 項目（正確）
```

**3. 段落間沒有空行**
```markdown
第一段
第二段（這樣會在同一段）

第一段

第二段（正確，有空行）
```

**4. 程式碼區塊語言標籤拼錯**
````markdown
```pyhon  ← 錯字，不會有語法高亮
```python ← 正確
````

**5. 表格格式缺 `|`**
```markdown
欄一 欄二（錯誤）
|欄一|欄二|（正確）
```

### ⚠️ 平台差異注意

- **任務清單** `- [ ]` — GitHub 支援，部分平台不支援
- **表格** — 標準 Markdown 不含，CommonMark 擴充才有
- **腳註** — GitHub、Obsidian 支援，其他平台不一定
- **數學公式** — 需要 MathJax 或 KaTeX 支援

### 💡 最佳實踐

1. 一份文件只使用一個 H1 標題
2. 標題層級不要跳過（不要從 H1 直接跳到 H4）
3. 程式碼一律使用程式碼區塊，不要用引號
4. 連結文字要有意義（不要寫「點這裡」）
5. 圖片一定要加替代文字（Alt Text）

---

## 16. 速查表 Cheat Sheet

```
## 文字格式
**粗體**          *斜體*           ***粗斜體***
~~刪除線~~        `行內程式碼`

## 標題
# H1   ## H2   ### H3   #### H4   ##### H5   ###### H6

## 清單
- 無序清單        1. 有序清單       - [ ] 任務清單

## 連結與圖片
[文字](URL)       ![Alt](圖片URL)

## 區塊
> 引用            --- 分隔線

## 表格
| 欄1 | 欄2 |
|-----|-----|
| 值1 | 值2 |

## 程式碼
`行內`
​```語言
程式碼區塊
​```

## 進階
[^1] 腳註         ==highlight==     $數學公式$
```

---

## 延伸學習資源

- [CommonMark 規格書](https://commonmark.org/) — Markdown 標準規範
- [GitHub Flavored Markdown](https://github.github.com/gfm/) — GitHub 擴充語法
- [Markdown Guide](https://www.markdownguide.org/) — 完整學習指南
- [Anthropic Academy](https://www.anthropic.com/academy) — AI 使用技巧

---

*本教材為「好好用 AI」課程補充教材 | CC BY-SA 4.0 | 2026*
