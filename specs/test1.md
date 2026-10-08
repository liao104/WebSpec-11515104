# 綠天咖啡網站｜逆向詳細規格

> 來源檔案：`WebPage/refined/index.html`  
> 文件用途：將目前已完成的單頁形象網站逆向轉化為可維護、可精確修改與可重新實作的規格文件。  
> 來源版本 SHA-256：`C3CFFDC3880D527F55BC6148CC3C1AAB5A5A31D6E87AEE0333D5BCB396ABBE1F`

---

## 1. 專案概述

| 項目 | 規格 |
|---|---|
| 品牌名稱 | 綠天咖啡（GREEN SKY COFFEE） |
| 網站類型 | 精品手沖咖啡品牌的一頁式形象／產地選豆導覽網站 |
| 語言 | 繁體中文，HTML `lang="zh-Hant"` |
| 目標受眾 | 重視咖啡品質、喜愛單一產區風土、追求日常手沖儀式感與自然質感的消費者 |
| 主要目標 | 建立清新自然的品牌形象、引導探索當季產區單品選豆、傳遞手沖萃取理念、促成風味收藏與門市體驗預約 |
| 網頁形式 | 單一 `index.html`，CSS 與 JavaScript 皆內嵌於文件中；不依賴外部後端或建置打包工具 |
| 品牌核心語句 | 「從產地，到杯中的一片綠。」 |

### 1.1 品牌語氣與視覺調性

- **文字語調**：沉靜、真誠、注重風土與工藝細節。避免強勢促銷或誇張文案，以「產地、風土、高海拔、晨霧、陽光、慢熟、小批次、手沖、呼吸」等自然意象描寫咖啡旅程。
- **排版氛圍**：留白寬闊、呼吸感強，大量採用大地色系與大地綠調，呈現如同森林微風與宣紙質地的溫潤手感。
- **英文輔助文案**：以等寬字體（`DM Mono`）呈現，字距加寬、簡潔俐落，帶有專業烘焙與咖啡實驗室筆記的精確感。

---

## 2. 文件與技術邊界

- **前端標準**：HTML5、原生 CSS3、原生 JavaScript（ES6+）。
- **架構限制**：全頁僅包含 1 個 `<style>` 與 1 個 `<script>` 區塊，完全不依賴外部 CSS/JS 庫或打包工具（如 Tailwind、Bootstrap、jQuery 等）。
- **外部字型資源**：僅引用 Google Fonts：
  - `DM Mono`（權重 400, 500）
  - `Noto Sans TC`（權重 400, 500, 600, 700）
  - `Noto Serif TC`（權重 500, 600, 700, 900）
- **圖像與視覺元素**：**全站完全不使用任何外部圖檔（無 jpg/png/webp）**。所有圖形皆由純 CSS 形狀、漸層、陰影、SVG 偽元素、邊框與 `clip-path` 多邊形遮罩繪製（包含品牌果葉標記、Hero 山林植株日盤、產地之窗、三款立體豆袋、手沖 V60 壺線稿與門市資訊卡）。
- **頁面骨幹**：包含 1 個固定頁首 Header、5 個主要 `<section>`、3 個選豆商品 `<article>`、1 個門市資訊卡 `<aside>`、1 個 Footer 與 1 個固定定位的動態 Toast。
- **導覽機制**：頁面內所有導覽連結皆為同頁錨點平滑捲動（`#top`, `#story`, `#selection`, `#brew`, `#visit`）。

---

## 3. SEO 與基礎文件設定

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="綠天咖啡以小批次烘焙與手沖，讓每一支精品咖啡豆的產地風土清晰抵達杯中。">
  <title>綠天咖啡｜從產地，到杯中的一片綠</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Noto+Sans+TC:wght@400;500;600;700&family=Noto+Serif+TC:wght@500;600;700;900&display=swap" rel="stylesheet">
</head>
```

- **全域文字與字型指定**：
  - `body`：預設使用 `Noto Sans TC`，字級基準 16px，行高 1.7，平滑字型渲染（`-webkit-font-smoothing: antialiased;`）。
  - 主要展示標題與卡片名稱：使用 `Noto Serif TC`。
  - 英文小標、海拔、參數、價格、按鈕字距：使用 `DM Mono`。
- **捲動行為**：`html` 預設啟用 `scroll-behavior: smooth`。
- **動態偏好**：當偵測到使用者偏好減少動態（`prefers-reduced-motion: reduce`）時，強制將 `scroll-behavior` 設為 `auto`、動畫與轉場秒數降至極限，所有進場元素直接顯示。
- **焦點樣式**：全站所有可聚焦元素（連結、按鈕、輸入框）皆需具備明確可見的 `:focus-visible` 樣式：`outline: 3px solid #d3c66b; outline-offset: 3px;`。

---

## 4. 視覺系統規格

### 4.1 色彩 Token（CSS Variables）

| Token 名稱 | 色碼 | 角色與用途說明 |
|---|---:|---|
| `--forest` | `#17382b` | 主品牌色（森林綠）。Hero、Brew 區塊背景、深色標籤、豆袋底色 |
| `--deep-forest` | `#0e291f` | 最深森林墨綠。頁尾背景、主要按鈕字色、Toast 浮層背景 |
| `--moss` | `#426a4a` | 苔蘚綠。次要標題重點、小標字色、門市卡底色、文字按鈕色 |
| `--leaf` | `#9aaa72` | 嫩葉綠。導覽底線、裝飾線條、高光點綴 |
| `--cream` | `#f4f1e8` | 奶油米色。頁面主背景色、產地選豆區背景色 |
| `--paper` | `#fbfaf5` | 宣紙淺白。品牌理念、門市區背景色、選豆卡片底色 |
| `--oat` | `#ddca9e` | 燕麥暖色。主按鈕背景色、Toast 左側重點邊線、暖色裝飾 |
| `--clay` | `#ad7655` | 陶土紅棕。按鈕 hover 狀態、咖啡果實漸層點綴色 |
| `--ink` | `#26342b` | 墨綠深字。淺色背景區主要段落與標題文字 |
| `--muted` | `#69776e` | 灰綠色。次要段落文字、產地資訊說明 |
| `--line` | `#d9ddd1` | 分隔線、卡片下邊框、表格分隔線 |
| `--shadow` | `0 20px 50px rgba(18, 45, 32, .13)` | 全站共用深綠底蘊柔和陰影 |

### 4.2 字體排印（Typography）

| 元件類型 | 指定字體 | 規格與細節 |
|---|---|---|
| 一般內文、段落 | Noto Sans TC | 14px–16px，行高 1.7–1.9，顏色 `--ink` 或 `--muted` |
| Eyebrow 小標（區塊前導） | DM Mono | 11px、權重 500、字距 `.12em`，前方附帶 26px 細橫線 |
| 區塊標題（Section Title） | Noto Serif TC | `clamp(30px, 4vw, 48px)`，行高 1.3，字距 `.06em`，重點詞使用 `<strong>` 套用 `--moss` |
| Hero 主視覺標題 | Noto Serif TC | `clamp(43px, 5.5vw, 70px)`，權重 900，行高 1.22，字距 `.08em`，結尾關鍵詞以 `<em>` 套用淡金綠 `#d2dfa9` |
| 參數、編號、海拔、價格 | DM Mono | 10px–15px，權重 400–500，字距 `.08em` 至 `.14em` |
| 咖啡豆名稱標題 | Noto Serif TC | 23px，權重 700，行高 1.4，字距 `.06em` |
| 螢幕閱讀器專用隱藏類別 | `.sr-only` | `position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0,0,0,0);` |

### 4.3 版面佈局與通用尺寸

- **主要容器（`.container`）**：
  - 桌面版：`width: min(1140px, calc(100% - 52px)); margin: 0 auto;`
  - 手機版（<= 570px）：`width: min(100% - 34px, 1140px);`（左右留白 17px）
- **主要大型區塊垂直間距**：
  - 桌面版上下 padding 約 112px–118px；
  - 手機版（<= 570px）統一降為 76px。
- **按鈕通用樣式（`.button`）**：
  - 最小高度 50px，內距 `12px 22px`，圓角 1px（俐落精品感），字級 14px，字距 `.04em`，`font-weight: 700`。
  - 主按鈕（`.button-main`）：背景 `--oat`，文字 `--deep-forest`，陰影 `0 10px 24px rgba(7, 27, 18, .18)`，hover 時背景轉為 `#eddaac` 並上浮 2px。
  - 次按鈕（`.button-light`）：透明背景，邊框 `rgba(255,255,255,.58)`，白字，hover 時背景呈現微透明白 `rgba(255,255,255,.12)`。

---

## 5. 頁面資訊架構與內容規格

### 5.1 頁首與導覽列（Header & Navigation）

#### DOM 結構

```text
header.header#top
└─ nav.nav.container[aria-label="主要導覽"]
   ├─ a.brand[href="#top"][aria-label="回到綠天咖啡首頁"]
   │  ├─ span.brand-symbol[aria-hidden="true"]
   │  └─ span
   │     ├─ "綠天咖啡"
   │     └─ small "GREEN SKY COFFEE"
   ├─ button.menu-button[type="button"][aria-label="開啟導覽選單"][aria-expanded="false"][aria-controls="navLinks"] "☰"
   └─ div.nav-links#navLinks
      ├─ a[href="#story"] "咖啡介紹"
      ├─ a[href="#selection"] "產地選豆"
      ├─ a[href="#brew"] "沖煮特色"
      └─ a.nav-book[href="#visit"] "門市資訊"
```

#### 視覺與互動規範

- 絕對定位疊加於 Hero 頂端，寬度 100%，高度 76px（行動版 68px），底部帶有半透明細線 `1px solid rgba(255,255,255,.17)`。
- **品牌 Logo 標記（`.brand-symbol`）**：
  - 寬 29px、高 31px，邊框 `1px solid #bbcd91`，圓角 `50% 50% 47% 47%`（呈現果實與葉脈輪廓）。
  - 內部 `::before` 偽元素繪製一條傾斜 32 度的葉脈中心線。
- **導覽連結互動**：
  - 一般連結文字 13px，hover 時自右向左平滑展開嫩葉綠底線（`scaleX(1)`，過渡 0.2 秒）。
  - 「門市資訊」（`.nav-book`）為線框 CTA 按鈕，內距 `8px 15px`，邊框 `rgba(255,255,255,.58)`，hover 時反白為白底綠字。
- **手機版行為（<= 840px）**：
  - 顯示漢堡按鈕 `.menu-button`。
  - `.nav-links` 轉為絕對定位下拉抽屜，底色為深綠 `#112f23`，以 `max-height: 0` 至 `300px` 動畫展開。
  - 點擊按鈕時切換圖示 `☰` ↔ `×`，並同步切換 `aria-expanded` 與 `aria-label`（「開啟導覽選單」/「關閉導覽選單」）。
  - 點擊任一導覽項目後，選單自動收合並復原按鈕狀態。

---

### 5.2 品牌首頁主視覺（Hero）

#### 版面與參數

| 項目 | 規格細節 |
|---|---|
| 區塊標籤 | `<section class="hero" aria-labelledby="heroTitle">` |
| 尺寸高度 | 桌面最小高度 720px；中型螢幕 725px；手機版 680px |
| 版面結構 | 桌面版雙欄格線 `1.05fr / .95fr`，間距 35px，上下內距 `126px 0 72px` |
| 背景效果 | 深森林綠 `--forest`，搭配右上方柔和徑向光暈，以及右上延伸的 650px 多重同心圓弧光 |
| 底部元件 | 左下角附帶捲動提示 `<p class="scroll-hint">SCROLL TO EXPLORE</p>`（前附 36px 細線） |

#### 左欄文案規格

- **Eyebrow 小標**：`SMALL BATCH · SPECIALTY COFFEE`（色碼 `#c3d99a`）
- **H1 標題**：
  ```html
  <h1 id="heroTitle">從產地，<br>到杯中的<br><em>一片綠。</em></h1>
  ```
  （其中「一片綠。」以 `<em>` 包覆，顏色為淺金綠 `#d2dfa9`，無斜體）
- **說明段落（`.hero-lede`）**：`綠天咖啡以小批次烘焙與專注手沖，讓每一支咖啡豆的土壤、海拔與陽光，都在你的杯中留下清晰的痕跡。`
- **行動呼籲（CTA）**：
  - 主按鈕：`<a class="button button-main" href="#selection">品味本季選豆 <span class="icon-arrow">→</span></a>`
  - 次按鈕：`<a class="button button-light" href="#story">認識綠天</a>`
- **品牌宣言標記（`.hero-signature`）**：`GROWN WITH CARE · BREWED WITH PATIENCE`

#### 右欄純 CSS 插畫規格（`.hero-visual`）

- 使用純 CSS 建構，容器設定 `aria-hidden="true"`，高度 453px（平板 280px，手機 238px）：
  1. **晨曦日盤（`.sun-disc`）**：右上角 164px 圓形，淡金綠色 `#dce7b5`，附帶擴散光暈。
  2. **高地山嶺（`.hill`）**：透過 `clip-path: polygon(...)` 繪製多峰山丘，搭配雙層斜向漸層形成背光立體陰影。
  3. **咖啡植株（`.coffee-plant`）**：
     - 主莖枝（`.stem`）：棕金細線傾斜 12 度生長。
     - 5 片精細葉片（`.leaf-a` ~ `.leaf-e`）：以邊框、葉脈與漸層微透明背景組成，不同角度展開。
     - 3 顆成熟果實（`.bean-1` ~ `.bean-3`）：紅棕色漸層、立體陰影與中央縫線。
  4. **海拔數據標註（`.origin-tag`）**：
     - 內容：`1,850m`（DM Mono 粗體）、`高海拔慢熟`、`保留明亮酸質`。
     - 左側帶有 1px 嫩綠色裝飾線；手機版（<= 570px）自動隱藏以保持畫面清爽。

---

### 5.3 品牌理念：咖啡介紹（#story）

#### 版面與內容規格

| 項目 | 規格細節 |
|---|---|
| 區塊標籤 | `<section class="story" id="story" aria-labelledby="storyTitle">` |
| 背景顏色 | 宣紙淺白色 `--paper`（`#fbfaf5`） |
| 版面結構 | 桌面版兩欄 `.92fr / 1.08fr`，欄距依寬度為 `clamp(46px, 9vw, 120px)` |
| 左欄插畫 | 產地之窗（`.origin-window`），純 CSS 風景窗與左下浮貼深綠品牌卡 |
| 右欄文案 | 理念小標、大標題、兩段敘述文案與延伸連結 |

#### 內容明細

- **左側產地之窗（`.origin-window`，`aria-hidden="true"`）**：
  - 內部為淡灰綠底色，內縮 27px 裝飾邊框。
  - 包含產地金色太陽（`.origin-sun`）與雙重剪裁山峰（`.origin-hill-one`、`.origin-hill-two`）。
  - 右下產地文字：`HUILA, COLOMBIA` / `ALTITUDE 1,850M`。
  - 左下覆蓋深綠資訊卡（`.story-note`）：
    - 標題：`OUR STARTING POINT`（DM Mono 小標）
    - 內容：`每一杯的起點，都在一片認真生長的土地。`
- **右側文字敘述**：
  - 小標：`FROM SOIL TO CUP`
  - 標題：`我們想讓你喝見，<br>咖啡豆的<strong>來處</strong>。`（「來處」使用 `<strong>`，套用 `--moss`）
  - 段落一：`好的咖啡從不只是一串風味名詞。它來自高地的晨霧、果實成熟的速度，以及農人日復一日的照看。我們走近每個產區，只為把那些真實而細緻的不同，好好留在一杯咖啡裡。`
  - 段落二：`從選豆、烘焙到注水，少一點干擾，多一點尊重，讓風土自己說話。`
  - 文字連結：`<a class="story-link" href="#brew">看見我們的沖煮方式 <span>→</span></a>`

---

### 5.4 產地選豆（#selection）

#### 區塊配置

| 項目 | 規格細節 |
|---|---|
| 區塊標籤 | `<section class="selection" id="selection" aria-labelledby="selectionTitle">` |
| 背景顏色 | 奶油米色 `--cream`（`#f4f1e8`） |
| 標題配置 | 標題列橫向對齊（左為 Eyebrow + 標題，右為說明文案，手機版轉縱向） |
| 卡片排版 | 桌面 3 欄等寬格線；欄距 18px；卡片最小高度 455px，白色宣紙底 |
| 卡片互動 | hover 時整張卡片平滑上浮 6px，伴隨深森林綠陰影 `--shadow` |

#### 標題列文案

- Eyebrow：`SEASONAL COFFEE`
- 標題：`此刻，來自三座<strong>山的禮物</strong>。`（「山的禮物」套用 `--moss`）
- 說明段落：`為喜歡探索的人挑選三款單一產區；清爽、甜潤與醇厚，都有恰好的位置。`

#### 三款選豆卡片詳細規格表

| 序號與調性（`.card-index`） | 豆袋中文名 | 豆袋英文規格 | 卡片主名稱（`<h3>`） | 處理法與海拔（`.card-origin`） | 風味標籤（`.flavour span`） | 售價（`.price`） | 收藏按鈕 `data-coffee` | 豆袋視覺主題色 |
|---|---|---|---|---|---|---|---|---|
| `01 / BRIGHT & FLORAL` | 耶加雪菲 | `ETHIOPIA / WASHED` | 衣索比亞・耶加雪菲 | G1 水洗處理｜1,950m | 茉莉、柑橘、蜂蜜 | `NT$ 520 / 200g` | `衣索比亞・耶加雪菲` | 森林墨綠（`--forest`） |
| `02 / JUICY & VIVID` | 涅里 | `KENYA / WASHED` | 肯亞・涅里 | AA 水洗處理｜1,720m | 黑醋栗、洛神、紅糖 | `NT$ 580 / 200g` | `肯亞・涅里` | 橄欖草綠（`#315a3d`） |
| `03 / ROUND & SWEET` | 慧蘭 | `COLOMBIA / HONEY` | 哥倫比亞・慧蘭 | 蜜處理｜1,850m | 黃桃、焦糖、可可 | `NT$ 480 / 200g` | `哥倫比亞・慧蘭` | 陶土熟栗（`#806248`） |

- **豆袋純 CSS 繪製細節（`.bag-visual`）**：
  - 上方為純色背景展台（高度 214px），中央矗立立體咖啡豆袋（156px × 199px）。
  - 頂端附帶雙層白色半透明車縫線。
  - 豆袋中央繪製旋轉微型葉片圖章，下方為直書繁體中文豆名與英文產區/處理法字樣。
- **卡片按鈕**：
  - `<button class="save-button" type="button" data-coffee="{咖啡名稱}">收藏風味 ＋</button>`
  - 預設字色為苔蘚綠 `--moss`，hover 轉為陶土紅棕 `--clay`。
  - 點擊後不轉址，直接跳出客製化 Toast 提示。

---

### 5.5 沖煮特色（#brew）

#### 區塊配置

| 項目 | 規格細節 |
|---|---|
| 區塊標籤 | `<section class="brew" id="brew" aria-labelledby="brewTitle">` |
| 背景顏色 | 森林綠 `--forest`（`#17382b`），文字為米白 `#f8f8ef` |
| 背景裝飾 | 左上方 460px 半透明圓環與 75px 光暈圈 |
| 版面結構 | 桌面版兩欄 `1.02fr / .98fr`，間距 `clamp(45px, 8vw, 100px)` |
| 左欄內容 | 純 CSS 手沖線稿示意圖（`.brew-drawing`）與萃取參數標籤 |
| 右欄內容 | 理念小標、標題、說明與三個手沖工藝步驟清單 |

#### 左欄手沖線稿規格（`.brew-drawing`，`aria-hidden="true"`）

- 邊框帶有淡金綠色透明邊框，最小高度 409px（手機版 325px）：
  1. **左上裝飾條**：三條水平排列的細橫線。
  2. **注水弧線（`.water-lines`）**：三層同心圓弧頂水流線，象徵均勻注水擾動。
  3. **V60 濾杯（`.dripper`）**：梯形幾何多邊形剪裁，帶有斜向肋骨導流線條。
  4. **玻璃分享壺（`.server`）**：圓角壺底，下層注入半透明深棕色咖啡液（`.server::after`）。
  5. **萃取參數標示（`.brew-caption`）**：
     - `V60 / 15G : 240ML`
     - `92°C · 2'45''`

#### 右欄文字與步驟清單

- Eyebrow：`OUR BREWING RITUAL`（色碼 `#c6d99c`）
- 標題：`讓水走慢一些，<br>讓風味<strong>更完整</strong>。`（「更完整」使用 `<strong>` 套用 `#dce7b5`）
- 說明：`手沖不是一套僵硬的公式，而是一次與咖啡相處的過程。我們用穩定的節奏，萃取出飽滿甜感與乾淨尾韻。`
- **三步驟有序清單（`<ol class="method-list">`）**：
  - 每個步驟採左右兩欄網格（左 45px DM Mono 編號，右側為標題與說明），上下附帶淡綠色半透明分隔線：

| 步驟編號 | 步驟主旨（`<b>`） | 萃取細節說明（`<span>`） |
|---|---|---|
| `01` | 中細研磨，保留呼吸空間 | 15g 咖啡豆，讓香氣與水流找到平衡。 |
| `02` | 92°C 悶蒸，等待第一個訊號 | 30 秒浸潤，讓甜感從咖啡粉裡緩緩展開。 |
| `03` | 穩定注水，完成一杯清澈 | 240ml 水量，在 2 分 45 秒留下完整產地輪廓。 |

---

### 5.6 門市資訊（#visit）

#### 區塊配置

| 項目 | 規格細節 |
|---|---|
| 區塊標籤 | `<section class="visit" id="visit" aria-labelledby="visitTitle">` |
| 背景顏色 | 宣紙淺白色 `--paper` |
| 版面結構 | 桌面版兩欄 `1fr / 1fr`，間距 `clamp(42px, 8vw, 105px)` |
| 左欄內容 | 小標、標題、說明與 2×2 門市詳細資訊格線 |
| 右欄內容 | 綠天咖啡門市立體形象卡（`<aside class="store-card">`） |

#### 左欄門市資訊明細

- Eyebrow：`VISIT OUR BREW BAR`
- 標題：`到門市坐坐，<br>喝一杯剛剛好的<strong>綠意</strong>。`（「綠意」套用 `--moss`）
- 說明：`讓咖啡師依照你的喜好，帶你從香氣開始認識一支豆子。這裡有手沖、有對話，也有一段可以慢下來的午後。`
- **2×2 詳細資訊表格（`.details`）**：

| 欄位標籤（`<b>`，DM Mono） | 資訊內容（`<span>`） | 排版邊框細節 |
|---|---|---|
| `ADDRESS` | 台北市大安區青田街 28 號 | 奇數格（左欄），帶右側內距 19px |
| `OPENING HOURS` | 每日 10:00 — 19:00 | 偶數格（右欄），帶左邊線與左內距 19px |
| `BREW BAR` | 手沖咖啡・選豆諮詢 | 下方底邊線 |
| `CONTACT` | 02 2368 0828 | 下方底邊線、帶左邊線與左內距 19px |

#### 右欄門市形象卡片（`<aside class="store-card">`）

- 標籤宣告：`aria-label="綠天咖啡門市資訊卡"`
- 視覺：深苔蘚綠底色（`--moss`），飾以 45 度斜向條紋光澤與 265px 圓形光環，高度至少 350px。
- 內容：
  - Kicker：`GREEN SKY BREW BAR`（淡金綠色，DM Mono）
  - 大標題：`在城市裡，<br>留一小片山林。`（Noto Serif TC，31px）
  - 說明：`沿著青田街的樹影走進來，讓我們為你沖一杯此刻最適合的咖啡。`
  - 預約連結：`<a class="store-link" href="mailto:hello@greensky.coffee">預約選豆與手沖體驗 <span class="icon-arrow">→</span></a>`

---

### 5.7 頁尾（Footer）

#### 版面與內容規格

| 項目 | 規格細節 |
|---|---|
| 區塊標籤 | `<footer>` |
| 背景顏色 | 最深森林綠 `--deep-forest`（`#0e291f`），文字為淺白 `rgba(255,255,255,.68)` |
| 欄位排版 | 上層為三欄網格 `1.6fr / 1fr / 1fr`，間距 42px；下層為版權資訊底列 |

#### 欄位詳細內容

1. **品牌欄（`.footer-brand`）**：
   - 品牌標記與名稱：`<a class="brand" href="#top"><span class="brand-symbol" aria-hidden="true"></span><span>綠天咖啡<small>GREEN SKY COFFEE</small></span></a>`
   - 品牌小語：`從一顆用心生長的咖啡果實，到你手上安靜的一杯。`
2. **主題導覽（`EXPLORE`）**：
   - 標題：`EXPLORE`（DM Mono 小標，色碼 `#c6d99c`）
   - 清單連結：
     - `<a href="#story">咖啡介紹</a>`
     - `<a href="#selection">產地選豆</a>`
     - `<a href="#brew">沖煮特色</a>`
3. **聯絡資訊（`CONTACT`）**：
   - 標題：`CONTACT`（DM Mono 小標）
   - 清單項目：
     - `<a href="mailto:hello@greensky.coffee">hello@greensky.coffee</a>`
     - `台北市大安區青田街 28 號`
     - `每日 10:00 — 19:00`
4. **版權底列（`.footer-bottom`）**：
   - 頂部帶有細邊框 `1px solid rgba(255,255,255,.13)`。
   - 左側：`© 2026 GREEN SKY COFFEE. ALL RIGHTS RESERVED.`
   - 右側標語：`GROWN SLOW · BREWED CLEAR`

---

## 6. 互動與 JavaScript 行為規格

### 6.1 手機導覽抽屜（Mobile Navigation）

- **觸發按鈕**：`.menu-button`，初始文字為 `☰`，`aria-expanded="false"`，`aria-label="開啟導覽選單"`，`aria-controls="navLinks"`。
- **斷點生效**：螢幕寬度 `<= 840px` 時顯示。
- **展開狀態**：
  - 點擊按鈕切換 `.nav-links.open`。
  - 選單由 `max-height: 0` 平滑過渡至 `300px`。
  - 按鈕內容切換為 `×`，`aria-expanded` 設為 `"true"`，`aria-label` 設為 `"關閉導覽選單"`。
- **收合狀態**：
  - 點擊開啟狀態的按鈕或點擊任一導覽項目（`.nav-links a`）時，立刻移除 `.open`。
  - 按鈕內容復原為 `☰`，`aria-expanded` 設為 `"false"`，`aria-label` 設為 `"開啟導覽選單"`。

### 6.2 Toast 即時回饋通知

- **DOM 結構**：
  ```html
  <div class="toast" id="toast" role="status" aria-live="polite"></div>
  ```
- **視覺外觀**：固定於視窗右下角（`right: 22px; bottom: 22px;`），深森林綠底色，左側 3px 燕麥色邊框（`--oat`），白色文字，深色立體陰影。
- **動畫狀態**：
  - 預設：`opacity: 0; pointer-events: none; transform: translateY(12px);`
  - 顯示時（`.show`）：`opacity: 1; transform: translateY(0);`（轉場時間 0.23 秒）
- **生命週期**：
  - 呼叫 `showToast(message)` 時顯示，並在 **2600 毫秒（2.6 秒）** 後自動隱藏。
  - 連續點擊時，必須先執行 `window.clearTimeout(toastTimer)` 清除既有計時器，避免提示過早消失。
- **觸發行為**：
  - 點擊三款選豆卡片中的「收藏風味 ＋」按鈕（帶有 `data-coffee` 屬性）：
  - 提示訊息：`已收藏「{咖啡名稱}」，下次來門市時可以問問它。`

### 6.3 捲動進場動態（Scroll Reveal）

- **目標元素**：所有標記 `.reveal` 類別的區塊與卡片。
- **樣式設定**：
  - 初始狀態：`opacity: 0; transform: translateY(18px); transition: opacity .65s ease, transform .65s ease;`
  - 觸發進場：加上 `.in` 類別，`opacity: 1; transform: translateY(0);`
- **IntersectionObserver 規格**：
  - 觀察門檻：`threshold: .12`。
  - 進入視窗時加上 `.in`，並立即呼叫 `observer.unobserve(entry.target)` 停止監聽，保證動態僅執行一次。
- **降級與無障礙備援**：
  - 若瀏覽器不支援 `IntersectionObserver`，或使用者系統開啟減動態偏好（`prefers-reduced-motion: reduce`），則在初始化時直接對所有 `.reveal` 元素加入 `.in`，確保內容正常可見。

---

## 7. 響應式規格（Responsive Breakpoints）

### 7.1 中型螢幕（平板裝置，`max-width: 840px`）

- **導覽列**：高度降為 68px，隱藏橫向選單，顯示漢堡按鈕，下拉選單具備深綠背景與分割線。
- **Hero 主視覺**：
  - 雙欄改為單欄縱向排列，上方留白設為 110px，最小高度 725px。
  - 右側插畫高度縮為 280px（負 margin 向上貼近文案），咖啡植株整體縮放 `scale(.75)`。
- **主要內容區塊**：
  - 品牌理念（`.story-grid`）、手沖日常（`.brew-grid`）與門市（`.visit-grid`）均由兩欄改為單欄。
  - 產地之窗（`.origin-window`）寬度設為最大 560px 居中。
- **產地選豆網格**：由 3 欄改為 2 欄，第 3 款咖啡（哥倫比亞・慧蘭）橫跨兩欄（`grid-column: span 2;`）。
- **頁尾**：改為兩欄（`1.4fr 1fr`），品牌欄橫跨全寬（`grid-column: span 2;`）。

### 7.2 小型螢幕（手機裝置，`max-width: 570px`）

- **全域邊距**：容器寬度改為 `min(100% - 34px, 1140px)`，兩側各保留 17px。
- **主視覺 Hero**：
  - 最小高度 680px，H1 標題字級固定為 40px，內文縮為 14px。
  - 插畫高度降為 238px，**完全隱藏海拔標籤（`.origin-tag { display: none; }`）**。
  - 捲動提示位置移至 `bottom: 12px; left: 17px;`。
- **區塊留白**：Story、Selection、Brew、Visit 上下留白全面縮減至 76px。
- **品牌理念 Story**：產地之窗高度降為 335px，深綠註記卡縮為 190px、內距 16px。
- **產地選豆 Selection**：
  - 標題列改為垂直排列（標題在上、說明在下）。
  - 選豆卡片全部轉為單欄（`grid-template-columns: 1fr;`），第 3 張卡片取消跨欄。
- **手沖日常 Brew**：線稿高度縮為 325px，水流、濾杯與分享壺等比例縮放為 `scale(.8)` 至 `scale(.82)`。
- **門市資訊 Visit**：四格資訊欄轉為單欄，清除原本奇偶項目的左右邊框與內距。
- **頁尾 Footer**：全面改為單欄，底部版權文字與品牌標語垂直分行排列。

---

## 8. 無障礙與可用性規格（Accessibility）

1. **語系與編碼宣告**：根節點嚴格指定 `<html lang="zh-Hant">`，編碼宣告 `<meta charset="UTF-8">`。
2. **語意化標籤層級**：
   - 完整採用 HTML5 語意元素：`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`。
   - 嚴格維持標題結構：唯一 `<h1>`（Hero）→ 區塊 `<h2>`（Story, Selection, Brew, Visit）→ 商品名稱與卡片標題 `<h3>`。
3. **無障礙標籤與對齊**：
   - 導覽區宣告 `aria-label="主要導覽"`。
   - 各區塊均以 `aria-labelledby` 正確綁定各自的區塊標題 id。
   - 門市卡宣告 `aria-label="綠天咖啡門市資訊卡"`。
   - 漢堡按鈕具備動態 `aria-expanded`、`aria-controls` 與動態切換的 `aria-label`。
4. **裝飾性圖形隱藏**：所有純 CSS 視覺容器（Hero 插畫、產地之窗、豆袋圖章、手沖線稿）均指定 `aria-hidden="true"`，避免螢幕閱讀器解析混亂。
5. **鍵盤導覽與可見焦點**：所有按鈕、超連結與可操作控制項皆具備高對比清晰的焦點框（`:focus-visible`）。
6. **動態狀態播報**：Toast 浮層具備 `role="status"` 與 `aria-live="polite"`，確保視障使用者加入收藏時可即時獲知語音回饋。
7. **減動態支援（prefers-reduced-motion）**：偵測到作業系統減動態需求時，停用平滑捲動，將全站動態縮減至最小並立即顯示進場內容。

---

## 9. 後續修改與維護指南

### 9.1 最常修改的位置對照

| 修改需求 | 應修改的 HTML / CSS 位置 |
|---|---|
| **品牌名稱與英文標語** | Header `.brand`、Hero `.hero-signature`、Footer `.footer-brand` 與版權列 |
| **Hero 宣言與主標題** | `#heroTitle`、`.hero-lede`、按鈕文字與 `.hero-actions` |
| **當季咖啡豆品項與售價** | `#selection` 內的三個 `.coffee-card`：`<h3>`、`.card-origin`、`.flavour`、`.price`、豆袋文字，以及按鈕 `data-coffee` 屬性 |
| **沖煮參數與工藝步驟** | `#brew` 的 `.brew-caption`（濾杯比例）與 `.method-list` 內各步驟標題與說明 |
| **門市地址、營業時間與電話** | `#visit` 的 `.details` 欄位與 Footer 的 `CONTACT` 清單 |
| **品牌調性主色彩** | CSS `:root` 中的色彩 Token（特別是 `--forest`, `--moss`, `--leaf`, `--oat`），請避免直接修改局部 hard-coded 色碼 |
| **純 CSS 插畫造形** | 各區塊對應的視覺 class（如 `.sun-disc`, `.coffee-plant`, `.bag`, `.dripper` 等） |

### 9.2 修改時的不可破壞條件

1. **不可移除核心錨點 id**：`#top`, `#story`, `#selection`, `#brew`, `#visit` 不得任意更名或刪除，否則導覽與平滑捲動將失效。
2. **不可移除 Toast 屬性**：Toast 的 `role="status"`、`aria-live="polite"` 以及按鈕上的 `data-coffee` 不得移除，否則收藏提示與無障礙宣告會中斷。
3. **保持自足無外部圖片依賴**：本專案設計核心為「純 CSS 幾何向量呈現與輕量快速載入」，除非規格另有更新，切勿直接以未經授權的外部圖檔替換 CSS 插畫。
4. **保持減動態處理**：修改進場動態或 CSS 轉場時，務必保留 `@media (prefers-reduced-motion: reduce)` 與 JavaScript 降級判斷。

---

## 10. 驗收清單（Acceptance Checklist）

- [ ] **文件宣告**：`lang="zh-Hant"`、UTF-8 編碼、viewport 與 Google Fonts 連結完整載入。
- [ ] **導覽與頁首**：Header 絕對定位疊於 Hero 上，桌面導覽連結 hover 底線由右至左延伸，門市資訊為線框按鈕。
- [ ] **行動導覽**：在 840px 以下切換為漢堡按鈕，展開/收合帶平滑動畫，同步變更圖示（☰ / ×）與 aria 屬性，點擊連結後自動收合。
- [ ] **Hero 主視覺**：雙色標題正常渲染，CSS 日盤、山巒、咖啡植株與果實位置正確，海拔標籤於手機版自動隱藏。
- [ ] **品牌理念（#story）**：產地之窗幾何山巒與左下深綠卡片顯示正常，理念文案與連結階層無誤。
- [ ] **產地選豆（#selection）**：三款選豆（衣索比亞・耶加雪菲、肯亞・涅里、哥倫比亞・慧蘭）之豆袋視覺、風味標籤、售價呈現正確。
- [ ] **選豆收藏互動**：點擊任一「收藏風味 ＋」按鈕，右下角能跳出包含該咖啡名稱的專屬 Toast，2.6 秒後自動收合。
- [ ] **手沖特色（#brew）**：CSS 繪製之同心圓水流、V60 濾杯與下壺比例正常，萃取三步驟與參數完整呈現。
- [ ] **門市資訊（#visit）**：2×2 門市資訊表格線條整齊，右側門市形象卡帶有預約 Email 連結。
- [ ] **頁尾（Footer）**：三欄資訊與版權列字距排版精確，包含導覽與聯絡項目。
- [ ] **響應式排版**：840px 以下選豆卡為 2 欄（第 3 款橫跨）；570px 以下選豆卡為單欄，四格門市資訊轉為單欄。
- [ ] **進場與減動態**：`.reveal` 元素依捲動淡入上移；若系統設定減動態，所有內容立即完整呈現。
- [ ] **無障礙檢測**：鍵盤 Tab 移動時具備高對比金黃色外框，純裝飾元件皆被螢幕閱讀器略過。

