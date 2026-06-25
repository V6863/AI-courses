# Everything You Must Know About Marp
### Marp 完全指南 — 好好用 AI 補充教材

> **適用對象：** 辦公室工作者、簡報製作者、AI 工具使用者  
> **學習目標：** 用 Markdown 寫出專業簡報，擺脫 PowerPoint 的排版束縛

---

## 目錄

1. [什麼是 Marp？](#1-什麼是-marp)
2. [為什麼選擇 Marp？](#2-為什麼選擇-marp)
3. [安裝與環境設定](#3-安裝與環境設定)
4. [第一份 Marp 簡報](#4-第一份-marp-簡報)
5. [投影片分頁語法](#5-投影片分頁語法)
6. [全域設定 Global Directives](#6-全域設定-global-directives)
7. [局部設定 Local Directives](#7-局部設定-local-directives)
8. [內建主題 Themes](#8-內建主題-themes)
9. [文字與格式](#9-文字與格式)
10. [圖片處理 Images](#10-圖片處理-images)
11. [背景圖片 Background Images](#11-背景圖片-background-images)
12. [多欄排版 Columns](#12-多欄排版-columns)
13. [程式碼展示 Code Blocks](#13-程式碼展示-code-blocks)
14. [數學公式 Math](#14-數學公式-math)
15. [匯出格式 Export](#15-匯出格式-export)
16. [自訂樣式 Custom CSS](#16-自訂樣式-custom-css)
17. [Marp 與 AI 工具的結合](#17-marp-與-ai-工具的結合)
18. [常見錯誤與注意事項](#18-常見錯誤與注意事項)
19. [速查表 Cheat Sheet](#19-速查表-cheat-sheet)

---

## 1. 什麼是 Marp？

**Marp**（Markdown Presentation Ecosystem）是一套將 Markdown 轉換為簡報投影片的工具，由日本工程師 Yuki Hattori 開發。

```
你寫的 Markdown              →    輸出的簡報
---                          →    新的一張投影片
# 大標題                     →    投影片主標題
- 項目一                     →    條列內容
![bg](image.jpg)             →    背景圖片
```

**核心概念：** 用純文字控制簡報內容與結構，版本可用 Git 追蹤，AI 可直接生成。

### Marp 生態系組成

| 元件 | 說明 |
|------|------|
| **Marp Core** | 核心轉換引擎（底層） |
| **Marp for VS Code** | 最常用的編輯器擴充套件 |
| **Marp CLI** | 命令列工具，批次匯出 |
| **Marpit** | 建構 Marp 的框架（給開發者） |

---

## 2. 為什麼選擇 Marp？

### Marp vs. PowerPoint / Keynote

| 功能 | Marp | PowerPoint |
|------|:----:|:----------:|
| 純文字撰寫 | ✅ | ❌ |
| AI 直接生成 | ✅ | ❌ |
| Git 版本控制 | ✅ | ❌（二進位檔） |
| 跨平台一致性 | ✅ | ⚠️ 字型常跑版 |
| 匯出 PDF/HTML/PPTX | ✅ | ✅ |
| 複雜動畫效果 | ❌ | ✅ |
| 拖曳排版 | ❌ | ✅ |
| 學習成本 | 低（會 Markdown 即可） | 中 |

### 最適合 Marp 的場景

- 技術簡報、教學講義
- 需要版本控制的簡報（提案、報告）
- 用 AI 快速生成簡報初稿
- 程式碼展示（語法高亮完美支援）
- 團隊協作撰寫簡報

---

## 3. 安裝與環境設定

### 方法一：VS Code 擴充套件（推薦新手）

1. 開啟 VS Code
2. 按 `Ctrl+Shift+X` 開啟擴充套件市集
3. 搜尋 **"Marp for VS Code"**
4. 點擊安裝（作者：marp-team）
5. 開啟 `.md` 檔案後，右上角會出現簡報預覽按鈕

**預覽快捷鍵：**
```
Ctrl+Shift+V    → 開啟 Markdown 預覽
點擊右上角圖示   → 開啟 Marp 預覽（並排顯示）
```

### 方法二：Marp CLI（進階，可批次匯出）

```bash
# 需要先安裝 Node.js
npm install -g @marp-team/marp-cli

# 確認安裝成功
marp --version
```

### 方法三：線上工具（免安裝）

- **Marp Web** — https://web.marp.app （官方線上版）
- **HackMD** — 支援 Marp 語法，可即時協作

---

## 4. 第一份 Marp 簡報

建立一個 `.md` 檔案，加入以下內容：

```markdown
---
marp: true
theme: default
---

# 我的第一份 Marp 簡報

作者：你的名字  
日期：2026-06-25

---

## 第二張投影片

- 第一個重點
- 第二個重點
- 第三個重點

---

## 第三張投影片

這是結論。

謝謝！
```

**關鍵：**
- 最頂端的 `---` 區塊是 **Front Matter**（設定區）
- 後續每個 `---` 都是**換頁符號**
- `marp: true` 是啟用 Marp 的必要設定

---

## 5. 投影片分頁語法

### 基本換頁

```markdown
# 第一張投影片

內容在這裡。

---

# 第二張投影片

新的一頁從這裡開始。
```

### 換頁規則

| 語法 | 說明 |
|------|------|
| `---` | 換頁（同時是水平線） |
| `***` | 換頁（同時是水平線） |
| `___` | 換頁（同時是水平線） |
| 新的 `#` 標題 | **不會**自動換頁（需手動 `---`） |

> **注意：** 換頁符號前後都要有空行，否則可能被解讀為標題的底線樣式。

---

## 6. 全域設定 Global Directives

在 Front Matter（最頂端的 `---` 區塊）中設定，影響**整份簡報**：

```markdown
---
marp: true
theme: gaia
size: 16:9
paginate: true
header: "公司內部簡報"
footer: "2026 © 版權所有"
backgroundColor: "#ffffff"
color: "#333333"
---
```

### 全域設定一覽

| 設定 | 可選值 | 說明 |
|------|--------|------|
| `marp` | `true` | 啟用 Marp（必填） |
| `theme` | `default` `gaia` `uncover` | 套用主題 |
| `size` | `16:9` `4:3` `1:1` | 投影片比例 |
| `paginate` | `true` `false` | 顯示頁碼 |
| `header` | 字串 | 每頁頁首文字 |
| `footer` | 字串 | 每頁頁尾文字 |
| `backgroundColor` | 色碼 | 背景顏色 |
| `color` | 色碼 | 文字顏色 |
| `style` | CSS 字串 | 自訂樣式 |

---

## 7. 局部設定 Local Directives

用 `<!-- directive: value -->` 語法，只影響**當前投影片**：

```markdown
---

<!-- backgroundColor: #1a1a2e -->
<!-- color: white -->
<!-- paginate: skip -->

# 特殊樣式頁面

這張投影片有深色背景，不顯示頁碼。

---

# 下一張回到預設樣式

這裡背景又回到白色了。
```

### 用底線前綴套用到後續所有投影片

```markdown
<!-- _backgroundColor: #f0f0f0 -->
```

單底線 `_` = 只影響當前頁  
（沒有底線的全域版本則在 Front Matter 設定）

### 常用局部設定

| 設定 | 說明 |
|------|------|
| `<!-- class: lead -->` | 套用置中版型（gaia 主題） |
| `<!-- paginate: skip -->` | 此頁不計入頁碼 |
| `<!-- header: "" -->` | 此頁隱藏頁首 |
| `<!-- footer: "" -->` | 此頁隱藏頁尾 |
| `<!-- _backgroundColor: black -->` | 此頁黑色背景 |

---

## 8. 內建主題 Themes

Marp 內建三套主題：

### default — 簡潔白色

```markdown
---
marp: true
theme: default
---
```

適合：商業簡報、正式報告

### gaia — 活潑彩色

```markdown
---
marp: true
theme: gaia
---
```

適合：教學、分享會、創意提案

**gaia 專屬 class：**

```markdown
<!-- class: lead -->    → 內容置中（適合標題頁）
<!-- class: invert -->  → 反色（深色背景）
```

### uncover — 極簡風格

```markdown
---
marp: true
theme: uncover
---
```

適合：學術簡報、技術演講

### 主題預覽對比

| 主題 | 預設背景 | 標題顏色 | 風格 |
|------|---------|---------|------|
| default | 白 | 深藍 | 正式 |
| gaia | 淡色 | 橘/綠 | 活潑 |
| uncover | 白 | 黑 | 極簡 |

---

## 9. 文字與格式

Marp 完整支援 Markdown 文字語法：

```markdown
# 大標題（H1）
## 小標題（H2）
### 子標題（H3）

**粗體重點**   *斜體強調*   ~~刪除線~~   `程式碼`

- 無序清單項目
  - 縮排子項目

1. 有序清單
2. 第二項

> 引用區塊，適合放名言或重點摘要
```

### 投影片文字大小建議

| 元素 | 建議字體大小 |
|------|------------|
| H1 主標題 | 48–60px（Marp 自動處理） |
| H2 小標題 | 36–40px |
| 內文 | 24–28px |
| 腳注 / 說明 | 16–18px |

> **原則：** 一張投影片的文字量，讓觀眾 5 秒內能掌握重點。

---

## 10. 圖片處理 Images

### 基本插入

```markdown
![說明文字](圖片路徑或URL)
```

### 調整圖片大小

```markdown
![w:400px](image.jpg)           寬度 400px
![h:300px](image.jpg)           高度 300px
![w:50%](image.jpg)             寬度 50%
![w:400px h:300px](image.jpg)   同時指定寬高
```

### 圖片濾鏡效果

```markdown
![blur](image.jpg)              模糊
![brightness:1.5](image.jpg)    提亮
![grayscale](image.jpg)         灰階
![sepia](image.jpg)             復古棕色
![invert](image.jpg)            色彩反轉
![opacity:0.5](image.jpg)       半透明
![drop-shadow](image.jpg)       陰影
```

### 組合使用

```markdown
![w:300px blur brightness:1.2](photo.jpg)
```

---

## 11. 背景圖片 Background Images

這是 Marp 最強大的功能之一：

### 全頁背景

```markdown
![bg](background.jpg)
```

### 背景尺寸控制

```markdown
![bg cover](image.jpg)      覆蓋整個投影片（預設）
![bg contain](image.jpg)    完整顯示不裁切
![bg fit](image.jpg)        等比縮放填滿
![bg auto](image.jpg)       原始尺寸
![bg 80%](image.jpg)        指定百分比大小
```

### 背景加濾鏡

```markdown
![bg blur:5px](image.jpg)           模糊背景
![bg brightness:0.4](image.jpg)     調暗背景（文字更易讀）
![bg opacity:0.3](image.jpg)        半透明背景
```

### 左右分割版型（Split Layout）

```markdown
---

![bg left](image.jpg)

# 右側標題

右側放文字內容，左側是圖片。

---

![bg right:40%](image.jpg)

# 左側文字

`right:40%` 代表圖片佔 40% 寬度。

---
```

### 多張背景圖（並排）

```markdown
![bg](image1.jpg)
![bg](image2.jpg)
![bg](image3.jpg)
```

三張圖片會自動並排分割畫面。

---

## 12. 多欄排版 Columns

Marp 原生不支援多欄，但有幾種解決方法：

### 方法一：使用 HTML + CSS（最彈性）

```markdown
---
marp: true
---

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;">

<div>

### 左欄標題

- 左欄第一點
- 左欄第二點
- 左欄第三點

</div>

<div>

### 右欄標題

- 右欄第一點
- 右欄第二點
- 右欄第三點

</div>
</div>
```

### 方法二：左右分割背景圖搭配文字

```markdown
![bg left:40%](chart.png)

## 數據分析結果

- Q1 成長 23%
- Q2 成長 31%
- 全年目標達成率 94%
```

### 方法三：表格模擬欄位

```markdown
| 優點 | 缺點 |
|------|------|
| 快速製作 | 無法拖曳 |
| 版本控制 | 複雜動畫受限 |
| AI 可生成 | 初學曲線 |
```

---

## 13. 程式碼展示 Code Blocks

Marp 完整支援語法高亮，適合技術簡報：

````markdown
```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

print(greet("World"))
```

```javascript
const fetchData = async (url) => {
  const response = await fetch(url);
  return response.json();
};
```

```bash
# 安裝依賴並啟動服務
npm install
npm run dev
```

```sql
SELECT user_id, COUNT(*) as orders
FROM orders
WHERE created_at >= '2026-01-01'
GROUP BY user_id
ORDER BY orders DESC;
```
````

### 標示特定行（部分主題支援）

````markdown
```python {1,3-5}
line1 = "這行被標示"
line2 = "這行正常"
line3 = "這行被標示"
line4 = "這行被標示"
line5 = "這行被標示"
```
````

---

## 14. 數學公式 Math

Marp 支援 KaTeX 數學公式：

### 行內公式

```markdown
能量守恆定律：$E = mc^2$

夏普比率：$SR = \frac{R_p - R_f}{\sigma_p}$
```

### 獨立公式區塊

```markdown
$$
\sum_{i=1}^{n} x_i = \frac{n(n+1)}{2}
$$

$$
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
$$
```

> **啟用方式：** 在 Front Matter 加入 `math: katex` 或 `math: mathjax`

```markdown
---
marp: true
math: katex
---
```

---

## 15. 匯出格式 Export

### 在 VS Code 中匯出

1. 開啟含有 `marp: true` 的 `.md` 檔
2. 按 `Ctrl+Shift+P` 開啟命令面板
3. 輸入 `Marp: Export Slide Deck`
4. 選擇格式（PDF / HTML / PPTX / PNG / JPEG）

### 使用 Marp CLI 匯出

```bash
# 匯出為 PDF
marp slides.md --pdf

# 匯出為 HTML（單一檔案，可在瀏覽器開啟）
marp slides.md --html

# 匯出為 PowerPoint
marp slides.md --pptx

# 匯出為 PNG 圖片（每頁一張）
marp slides.md --images png

# 指定輸出路徑
marp slides.md -o output/presentation.pdf

# 批次匯出資料夾內所有簡報
marp --pdf *.md
```

### 各格式比較

| 格式 | 優點 | 缺點 | 適合場景 |
|------|------|------|---------|
| **PDF** | 通用、版面固定 | 無法編輯 | 正式提交、列印 |
| **HTML** | 可互動、超連結有效 | 需瀏覽器開啟 | 線上分享 |
| **PPTX** | 可用 PowerPoint 繼續編輯 | 複雜樣式可能跑版 | 交給他人修改 |
| **PNG/JPEG** | 通用圖片格式 | 不可互動 | 社群分享、縮圖 |

### HTML 簡報功能

匯出 HTML 後，在瀏覽器中：

```
→ / Space       下一張
← / Backspace   上一張
F               全螢幕
G               跳至特定頁
P               講者筆記模式（如果有設定）
```

---

## 16. 自訂樣式 Custom CSS

### 方法一：在 Front Matter 中嵌入

```markdown
---
marp: true
style: |
  section {
    font-family: "Microsoft JhengHei", sans-serif;
    background-color: #f8f9fa;
  }
  h1 {
    color: #2c3e50;
    border-bottom: 3px solid #3498db;
    padding-bottom: 10px;
  }
  strong {
    color: #e74c3c;
  }
  code {
    background-color: #ecf0f1;
    border-radius: 4px;
    padding: 2px 6px;
  }
---
```

### 方法二：建立自訂主題檔案

建立 `my-theme.css`：

```css
/* @theme my-theme */

@import 'default';

section {
  font-family: "Microsoft JhengHei", sans-serif;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

section.lead {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}
```

在 Front Matter 引用：

```markdown
---
marp: true
theme: my-theme
---
```

在 CLI 指定主題路徑：

```bash
marp --theme my-theme.css slides.md --pdf
```

### 常用 CSS 選擇器

| 選擇器 | 說明 |
|--------|------|
| `section` | 每張投影片的容器 |
| `section.lead` | 套用 lead class 的投影片 |
| `section:first-child` | 第一張投影片 |
| `h1, h2, h3` | 各級標題 |
| `header, footer` | 頁首頁尾 |
| `section::after` | 頁碼元素 |

---

## 17. Marp 與 AI 工具的結合

### 用 AI 直接生成 Marp 簡報

給 Claude / ChatGPT 的提示詞範本：

````markdown
請幫我用 Marp 格式生成一份簡報，主題是「[你的主題]」。

格式要求：
- Front Matter 包含：marp: true, theme: gaia, size: 16:9, paginate: true
- 共 8 張投影片
- 第一張：標題頁（含副標題與日期）
- 第 2-7 張：內容頁（每頁一個重點，搭配 2-4 個條列）
- 最後一張：結論與 Q&A

每張投影片之間用 --- 分隔。
程式碼範例請用適當的程式碼區塊。
````

### AI 生成後的優化流程

```
1. AI 生成初稿（約 30 秒）
      ↓
2. VS Code + Marp 預覽確認結構
      ↓
3. 調整文字量（每頁不超過 5 個條列）
      ↓
4. 加入背景圖片或調整主題色
      ↓
5. 匯出 PDF / PPTX
```

### 讓 AI 改善現有簡報

```markdown
以下是我的 Marp 簡報原始碼，請幫我：
1. 將每頁文字濃縮到 5 點以內
2. 在適當位置加入 ![bg right](placeholder.jpg) 的圖片佔位符
3. 把數據改用 Markdown 表格呈現

[貼上你的簡報原始碼]
```

### Marp + AI 的工作流程建議

| 任務 | 建議工具 |
|------|---------|
| 生成大綱 | Claude / ChatGPT |
| 轉換為 Marp 格式 | Claude / ChatGPT |
| 生成圖表說明文字 | Claude / ChatGPT |
| 尋找配圖 | Unsplash、Pexels（免費商用） |
| 最終排版微調 | VS Code + Marp 擴充套件 |
| 匯出 PDF | Marp CLI 或 VS Code |

---

## 18. 常見錯誤與注意事項

### ❌ 常見錯誤

**1. 忘記加 `marp: true`**
```markdown
---
theme: gaia     ← 沒有 marp: true，不會渲染為簡報
---
```
✅ 正確：
```markdown
---
marp: true
theme: gaia
---
```

**2. 換頁符號格式錯誤**
```markdown
-- （兩個橫線）← 不是換頁符號
```
✅ 正確：
```markdown
--- （三個橫線）
```

**3. 圖片路徑錯誤**
```markdown
![bg](C:\Users\Name\Desktop\image.jpg)  ← 絕對路徑，其他電腦無法顯示
```
✅ 正確（使用相對路徑）：
```markdown
![bg](./images/image.jpg)
```

**4. CSS 中文字型未指定備用字型**
```css
font-family: "某中文字型";  ← 沒有備用字型
```
✅ 正確：
```css
font-family: "Microsoft JhengHei", "PingFang TC", sans-serif;
```

**5. 投影片內容過多**
```markdown
# 標題

- 第一點：很長很長的說明文字...
- 第二點：又很長的說明文字...
- 第三點：更多文字...
- 第四點：還有更多...
- 第五點：繼續...
- 第六點：超出版面了...
```
✅ 解法：拆成兩頁，或使用 `font-size` 縮小字體

### ⚠️ 注意事項

- **PPTX 匯出限制：** 自訂 CSS 動畫和某些效果在 PPTX 中不支援
- **字型嵌入：** PDF 匯出時字型通常會嵌入，但 HTML 版本需確認系統有安裝對應字型
- **圖片連結：** 使用外部 URL 圖片時，離線簡報會無法顯示
- **背景圖片 + 深色文字：** 淺色圖片搭配深色文字可能對比不足，記得加 `brightness` 調暗背景

### 💡 最佳實踐

1. **一頁一重點** — 每張投影片只傳達一個核心訊息
2. **7×7 原則** — 每頁不超過 7 行，每行不超過 7 個字
3. **圖片統一放在 `images/` 資料夾** — 方便管理和分享
4. **版本控制** — 用 Git 管理 `.md` 檔案，PPTX 無法 diff
5. **先定主題色再寫內容** — 避免後期大改 CSS

---

## 19. 速查表 Cheat Sheet

```
## Front Matter 設定
---
marp: true
theme: default | gaia | uncover
size: 16:9 | 4:3 | 1:1
paginate: true
header: "頁首文字"
footer: "頁尾文字"
backgroundColor: "#ffffff"
math: katex
---

## 換頁
---    （三條橫線）

## 局部設定（HTML 註解）
<!-- backgroundColor: #333 -->
<!-- class: lead -->
<!-- paginate: skip -->
<!-- _color: white -->   （底線 = 只影響本頁）

## 圖片
![w:400px](img.jpg)              調整寬度
![h:300px](img.jpg)              調整高度
![bg](img.jpg)                   全頁背景
![bg left:40%](img.jpg)          左側 40% 背景
![bg right](img.jpg)             右側背景
![bg cover blur:3px](img.jpg)    覆蓋並模糊
![bg brightness:0.5](img.jpg)    調暗背景

## 主題 Class（gaia）
<!-- class: lead -->              置中版型
<!-- class: invert -->            反色

## CLI 匯出
marp slides.md --pdf
marp slides.md --html
marp slides.md --pptx
marp slides.md --images png
marp --theme my-theme.css slides.md -o out.pdf
```

---

## 延伸學習資源

- [Marp 官方文件](https://marp.app/) — 完整語法參考
- [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) — 擴充套件下載
- [Marp CLI GitHub](https://github.com/marp-team/marp-cli) — CLI 工具
- [Marpit 文件](https://marpit.marp.app/) — 進階客製化框架
- [Marp 主題範例](https://github.com/marp-team/marp-core/tree/main/themes) — 官方主題原始碼
- [Unsplash](https://unsplash.com/) — 免費商用背景圖片

---

*本教材為「好好用 AI」課程補充教材 | CC BY-SA 4.0 | 2026*
