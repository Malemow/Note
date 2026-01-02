# 語意化標籤 (Semantic Elements)

> HTML5 語意化標籤為網頁提供結構化的意義，不僅讓程式碼更易讀，也能提升 SEO 和無障礙性。

## 📑 目錄

- [`<header>` - 頁首/標題區](#header---頁首標題區)
- [`<nav>` - 導航區](#nav---導航區)
- [`<main>` - 主要內容](#main---主要內容)
- [`<article>` - 文章/獨立內容](#article---文章獨立內容)
- [`<section>` - 章節/區段](#section---章節區段)
- [`<aside>` - 側邊欄/附加內容](#aside---側邊欄附加內容)
- [`<footer>` - 頁尾](#footer---頁尾)
- [`<address>` - 聯絡資訊](#address---聯絡資訊)
- [`<time>` - 時間/日期](#time---時間日期)
- [`<mark>` - 標記/高亮](#mark---標記高亮)
- [語意化標籤選擇指南](#語意化標籤選擇指南)
- [完整網頁布局範例](#完整網頁布局範例)
- [SEO 最佳實踐](#seo-最佳實踐)
- [最佳實踐總結](#最佳實踐總結)

---

## 什麼是語意化標籤？

語意化標籤（Semantic Elements）是具有明確意義的 HTML 標籤，它們清楚地向瀏覽器和開發者描述其內容的用途。

### 為什麼要使用語意化標籤？

**優點：**

1. **提升 SEO**
   - 搜尋引擎更容易理解網頁結構
   - 提高搜尋排名
   - 更好的內容索引

2. **改善無障礙性**
   - 螢幕閱讀器能更好地導航網頁
   - 提供更好的使用者體驗

3. **程式碼可讀性**
   - 更清楚的程式碼結構
   - 更容易維護
   - 團隊協作更順暢

4. **未來相容性**
   - 符合現代網頁標準
   - 更好的跨平台支援

### 語意化 vs 非語意化

```html
<!-- ❌ 非語意化：使用 div 堆砌 -->
<div id="header">
  <div id="nav">
    <div class="menu-item">首頁</div>
  </div>
</div>
<div id="main">
  <div class="post">
    <div class="post-title">文章標題</div>
    <div class="post-content">內容...</div>
  </div>
</div>
<div id="footer">
  版權資訊
</div>

<!-- ✅ 語意化：使用適當的標籤 -->
<header>
  <nav>
    <a href="/">首頁</a>
  </nav>
</header>
<main>
  <article>
    <h1>文章標題</h1>
    <p>內容...</p>
  </article>
</main>
<footer>
  <p>版權資訊</p>
</footer>
```

---

## `<header>` - 頁首/標題區

### 說明
`<header>` 代表引介性內容或導航連結的容器，通常包含網站標誌、標題、導航選單等。

**注意**: `<header>` 可以在多個地方使用，不僅限於頁面頂部。

### 語法
```html
<header>
  <!-- 引介性內容 -->
</header>
```

### 常見用途

| 位置 | 用途 | 範例 |
|------|------|------|
| 頁面頂部 | 網站主標題、Logo、主導航 | 整個網站的頁首 |
| `<article>` 內 | 文章標題、作者、發布日期 | 部落格文章頁首 |
| `<section>` 內 | 區段標題和簡介 | 章節頁首 |

### 📌 程式碼範例

```html
<!-- 網站主頁首 -->
<header>
  <img src="logo.png" alt="公司 Logo">
  <h1>我的網站</h1>
  <nav>
    <a href="/">首頁</a>
    <a href="/about">關於</a>
    <a href="/contact">聯絡</a>
  </nav>
</header>

<!-- 文章的頁首 -->
<article>
  <header>
    <h1>HTML5 語意化標籤完整指南</h1>
    <p>作者: 張三 | 發布日期: 2026-01-02</p>
    <p class="summary">本文將介紹 HTML5 的所有語意化標籤...</p>
  </header>
  <p>文章內容...</p>
</article>

<!-- 區段的頁首 -->
<section>
  <header>
    <h2>產品特色</h2>
    <p>我們的產品具有以下優勢</p>
  </header>
  <ul>
    <li>特色 1</li>
    <li>特色 2</li>
  </ul>
</section>
```

### ✨ 示範效果

<header style="background: #f8f9fa; padding: 20px; border-bottom: 3px solid #007bff;">
  <h2 style="margin: 0 0 10px 0;">網站名稱</h2>
  <nav>
    <a href="#" style="margin-right: 15px;">首頁</a>
    <a href="#" style="margin-right: 15px;">關於</a>
    <a href="#" style="margin-right: 15px;">服務</a>
    <a href="#">聯絡</a>
  </nav>
</header>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 5+ | ✅ 4+ | ✅ 5+ | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 在主頁首中包含網站導航
- ✅ 使用標題標籤（`<h1>`-`<h6>`）建立層級
- ✅ 文章頁首應包含標題和元資訊
- ⚠️ 一個頁面可以有多個 `<header>`，但通常只有一個主頁首

### 使用注意事項

```html
<!-- ❌ 錯誤：在 header 或 footer 內再放 header -->
<header>
  <header>...</header> <!-- 不應該巢狀 -->
</header>

<!-- ❌ 錯誤：header 放在 footer 或 address 內 -->
<footer>
  <header>...</header> <!-- 不合適 -->
</footer>

<!-- ✅ 正確：header 在 article 內 -->
<article>
  <header>
    <h2>文章標題</h2>
  </header>
  <p>內容...</p>
</article>

<!-- ✅ 正確：多個獨立的 header -->
<header>主頁首</header>
<main>
  <article>
    <header>文章頁首</header>
  </article>
</main>
```

---

## `<nav>` - 導航區

### 說明
`<nav>` 標籤定義導航連結的區塊，用於主要的導航選單。

**重要**: 並非所有連結都需要放在 `<nav>` 中，只有主要的導航區塊才使用。

### 語法
```html
<nav>
  <!-- 導航連結 -->
</nav>
```

### 常見類型

| 類型 | 說明 | 範例 |
|------|------|------|
| 主導航 | 網站主選單 | 頁面頂部的導航列 |
| 次導航 | 區段內的導航 | 側邊欄導航 |
| 麵包屑 | 位置導航 | 首頁 > 分類 > 產品 |
| 分頁 | 頁碼導航 | 上一頁 1 2 3 下一頁 |
| 目錄 | 文章目錄 | 文章內的章節連結 |

### 📌 程式碼範例

```html
<!-- 主導航選單 -->
<nav>
  <ul>
    <li><a href="/">首頁</a></li>
    <li><a href="/products">產品</a></li>
    <li><a href="/about">關於我們</a></li>
    <li><a href="/contact">聯絡我們</a></li>
  </ul>
</nav>

<!-- 麵包屑導航 -->
<nav aria-label="麵包屑">
  <ol>
    <li><a href="/">首頁</a></li>
    <li><a href="/category">電子產品</a></li>
    <li><a href="/category/phones">手機</a></li>
    <li aria-current="page">iPhone 15</li>
  </ol>
</nav>

<!-- 文章目錄 -->
<nav aria-label="目錄">
  <h2>目錄</h2>
  <ul>
    <li><a href="#intro">簡介</a></li>
    <li><a href="#features">功能特色</a></li>
    <li><a href="#usage">使用方法</a></li>
    <li><a href="#conclusion">結論</a></li>
  </ul>
</nav>

<!-- 分頁導航 -->
<nav aria-label="分頁">
  <ul>
    <li><a href="?page=1" aria-label="上一頁">«</a></li>
    <li><a href="?page=1">1</a></li>
    <li><a href="?page=2" aria-current="page">2</a></li>
    <li><a href="?page=3">3</a></li>
    <li><a href="?page=3" aria-label="下一頁">»</a></li>
  </ul>
</nav>

<!-- 頁尾連結（通常不用 nav） -->
<footer>
  <p>
    <a href="/privacy">隱私政策</a> |
    <a href="/terms">服務條款</a>
  </p>
</footer>
```

### ✨ 示範效果

<nav style="background: #343a40; padding: 15px;">
  <ul style="list-style: none; margin: 0; padding: 0; display: flex; gap: 20px;">
    <li><a href="#" style="color: white; text-decoration: none;">首頁</a></li>
    <li><a href="#" style="color: white; text-decoration: none;">產品</a></li>
    <li><a href="#" style="color: white; text-decoration: none;">關於</a></li>
    <li><a href="#" style="color: white; text-decoration: none;">聯絡</a></li>
  </ul>
</nav>

<br>

<nav aria-label="麵包屑" style="padding: 10px; background: #f8f9fa;">
  <ol style="list-style: none; margin: 0; padding: 0; display: flex; gap: 10px;">
    <li><a href="#">首頁</a> →</li>
    <li><a href="#">產品</a> →</li>
    <li>當前頁面</li>
  </ol>
</nav>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 5+ | ✅ 4+ | ✅ 5+ | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 使用 `aria-label` 或 `aria-labelledby` 區分多個導航
- ✅ 使用 `aria-current="page"` 標示當前頁面
- ✅ 使用清楚的連結文字
- ✅ 鍵盤可導航（Tab 鍵）
- ⚠️ 不要過度使用 `<nav>`，只用於主要導航

### 使用注意事項

```html
<!-- ❌ 錯誤：所有連結都放 nav -->
<nav>
  <a href="/privacy">隱私政策</a> <!-- 這不是主要導航 -->
</nav>

<!-- ✅ 正確：只有主要導航用 nav -->
<nav>
  <a href="/">首頁</a>
  <a href="/products">產品</a>
</nav>
<footer>
  <a href="/privacy">隱私政策</a>
</footer>

<!-- ❌ 錯誤：沒有區分多個導航 -->
<nav>主選單</nav>
<nav>側邊選單</nav>

<!-- ✅ 正確：使用 aria-label 區分 -->
<nav aria-label="主選單">...</nav>
<nav aria-label="側邊選單">...</nav>
```

---

## `<main>` - 主要內容

### 說明
`<main>` 標籤代表文件的主要內容，每個頁面應該只有一個 `<main>` 元素。

**重要規則**:
- 每個頁面只能有一個 `<main>`（不可使用 `hidden` 屬性隱藏）
- 不能是 `<article>`, `<aside>`, `<footer>`, `<header>`, `<nav>` 的後代

### 語法
```html
<main>
  <!-- 頁面的主要內容 -->
</main>
```

### 📌 程式碼範例

```html
<!-- 基本結構 -->
<body>
  <header>
    <h1>網站標題</h1>
    <nav>導航選單</nav>
  </header>

  <main>
    <!-- 這裡是頁面的主要內容 -->
    <h2>頁面標題</h2>
    <p>主要內容...</p>
  </main>

  <footer>
    頁尾內容
  </footer>
</body>

<!-- 部落格文章頁 -->
<body>
  <header>
    <nav>導航</nav>
  </header>

  <main>
    <article>
      <h1>文章標題</h1>
      <p>文章內容...</p>
    </article>
  </main>

  <aside>側邊欄</aside>
  <footer>頁尾</footer>
</body>

<!-- 搜尋結果頁 -->
<body>
  <header>
    <form>搜尋表單</form>
  </header>

  <main>
    <h1>搜尋結果：HTML5</h1>
    <section>
      <h2>結果 1</h2>
      <p>描述...</p>
    </section>
    <section>
      <h2>結果 2</h2>
      <p>描述...</p>
    </section>
  </main>

  <footer>頁尾</footer>
</body>
```

### ✨ 示範效果

<div style="border: 2px solid #dee2e6; min-height: 200px;">
  <div style="background: #e9ecef; padding: 10px; border-bottom: 1px solid #dee2e6;">
    Header（頁首）
  </div>
  <main style="background: #fff3cd; padding: 20px; min-height: 150px;">
    <strong>Main（主要內容區）</strong>
    <p>這裡是頁面的核心內容</p>
  </main>
  <div style="background: #e9ecef; padding: 10px; border-top: 1px solid #dee2e6;">
    Footer（頁尾）
  </div>
</div>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 26+ | ✅ 21+ | ✅ 7+ | ✅ All | ✅ 12+ |

### 無障礙建議

- ✅ 每個頁面都應該有 `<main>`
- ✅ 螢幕閱讀器可以快速跳到主要內容
- ✅ 使用「跳到主要內容」連結
- ⚠️ 確保每頁只有一個可見的 `<main>`

### 使用注意事項

```html
<!-- ❌ 錯誤：多個 main -->
<main>內容 1</main>
<main>內容 2</main> <!-- 不允許 -->

<!-- ❌ 錯誤：main 在不當的位置 -->
<article>
  <main>...</main> <!-- main 不能在 article 內 -->
</article>

<!-- ✅ 正確：main 包含 article -->
<main>
  <article>...</article>
</main>

<!-- ✅ 正確：跳到主要內容連結 -->
<body>
  <a href="#main-content" class="skip-link">跳到主要內容</a>
  <header>...</header>
  <main id="main-content">
    內容...
  </main>
</body>
```

---

## `<article>` - 文章/獨立內容

### 說明
`<article>` 代表獨立的、可重複使用的內容區塊，即使脫離網頁其他部分仍然有意義。

### 語法
```html
<article>
  <!-- 獨立的內容 -->
</article>
```

### 適用場景

| 場景 | 說明 | 範例 |
|------|------|------|
| 部落格文章 | 完整的文章內容 | 技術教學文章 |
| 新聞報導 | 新聞內容 | 新聞網站的報導 |
| 論壇貼文 | 獨立的貼文 | 討論區的主題 |
| 產品卡片 | 產品資訊 | 電商的產品列表 |
| 評論 | 使用者評論 | 文章下方的留言 |
| 互動小工具 | 獨立功能 | 天氣小工具、計算器 |

### 📌 程式碼範例

```html
<!-- 部落格文章 -->
<article>
  <header>
    <h1>HTML5 語意化標籤指南</h1>
    <p>作者: 張三 | 日期: 2026-01-02</p>
    <p>分類: <a href="/category/web">網頁開發</a></p>
  </header>

  <p>語意化標籤是 HTML5 的重要特性...</p>

  <section>
    <h2>什麼是語意化？</h2>
    <p>內容...</p>
  </section>

  <section>
    <h2>為何重要？</h2>
    <p>內容...</p>
  </section>

  <footer>
    <p>標籤: #HTML5 #語意化 #網頁開發</p>
    <p>分享: [Facebook] [Twitter]</p>
  </footer>
</article>

<!-- 新聞列表 -->
<main>
  <h1>最新新聞</h1>

  <article>
    <h2><a href="/news/1">新聞標題 1</a></h2>
    <p>摘要...</p>
    <time datetime="2026-01-02">2026年1月2日</time>
  </article>

  <article>
    <h2><a href="/news/2">新聞標題 2</a></h2>
    <p>摘要...</p>
    <time datetime="2026-01-01">2026年1月1日</time>
  </article>
</main>

<!-- 產品卡片 -->
<article class="product-card">
  <img src="product.jpg" alt="產品名稱">
  <h3>產品名稱</h3>
  <p>產品描述...</p>
  <p class="price">NT$ 1,299</p>
  <button>加入購物車</button>
</article>

<!-- 巢狀 article（文章內的評論） -->
<article>
  <h1>主要文章標題</h1>
  <p>文章內容...</p>

  <section>
    <h2>評論</h2>

    <article>
      <header>
        <h3>使用者 A</h3>
        <time datetime="2026-01-02T10:00">2026-01-02 10:00</time>
      </header>
      <p>很棒的文章！</p>
    </article>

    <article>
      <header>
        <h3>使用者 B</h3>
        <time datetime="2026-01-02T11:30">2026-01-02 11:30</time>
      </header>
      <p>學到很多，謝謝分享。</p>
    </article>
  </section>
</article>
```

### ✨ 示範效果

<article style="border: 1px solid #dee2e6; padding: 20px; margin-bottom: 20px;">
  <header style="border-bottom: 1px solid #dee2e6; padding-bottom: 10px; margin-bottom: 15px;">
    <h3 style="margin: 0 0 5px 0;">網頁開發最佳實踐</h3>
    <p style="margin: 0; color: #6c757d; font-size: 0.9em;">作者: 張三 | 2026-01-02</p>
  </header>
  <p>在現代網頁開發中，使用語意化標籤是非常重要的...</p>
  <footer style="border-top: 1px solid #dee2e6; padding-top: 10px; margin-top: 15px; font-size: 0.9em; color: #6c757d;">
    標籤: #HTML5 #開發
  </footer>
</article>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 5+ | ✅ 4+ | ✅ 5+ | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 每個 `<article>` 應該有標題（`<h1>`-`<h6>`）
- ✅ 使用 `<header>` 包含元資訊
- ✅ 使用 `<footer>` 包含額外資訊
- ✅ 可以包含 `<section>` 來組織內容
- ⚠️ 內容應該是獨立且完整的

### 使用注意事項

```html
<!-- ❌ 錯誤：非獨立內容用 article -->
<article>
  <p>網站導航</p> <!-- 這不是獨立內容 -->
</article>

<!-- ✅ 正確：使用 nav -->
<nav>
  <p>網站導航</p>
</nav>

<!-- 問：什麼時候用 article vs section? -->

<!-- 用 article：內容可以獨立存在 -->
<article>
  <h2>獨立的部落格文章</h2>
  <p>這篇文章脫離網站仍有意義...</p>
</article>

<!-- 用 section：內容是文件的一部分 -->
<article>
  <h1>完整文章</h1>
  <section>
    <h2>章節 1</h2>
    <p>內容...</p>
  </section>
  <section>
    <h2>章節 2</h2>
    <p>內容...</p>
  </section>
</article>
```

---

## `<section>` - 章節/區段

### 說明
`<section>` 代表文件中的一個主題性區段，通常包含標題。

**與 `<article>` 的區別**:
- `<article>` = 獨立、可重複使用的內容
- `<section>` = 文件中的主題區段

### 語法
```html
<section>
  <h2>區段標題</h2>
  <!-- 區段內容 -->
</section>
```

### 適用場景

| 場景 | 說明 | 範例 |
|------|------|------|
| 頁面區段 | 網頁的主題區塊 | 「功能介紹」區段 |
| 文章章節 | 文章內的章節 | 「簡介」、「方法」、「結論」 |
| 分頁內容 | Tab 內容 | 標籤頁切換的內容 |
| 分組內容 | 相關內容分組 | 產品特色列表 |

### 📌 程式碼範例

```html
<!-- 基本 section -->
<section>
  <h2>關於我們</h2>
  <p>公司簡介...</p>
</section>

<!-- 文章內的章節 -->
<article>
  <h1>HTML5 完整指南</h1>

  <section>
    <h2>簡介</h2>
    <p>HTML5 是最新的 HTML 標準...</p>
  </section>

  <section>
    <h2>新功能</h2>
    <p>HTML5 引入了許多新功能...</p>
  </section>

  <section>
    <h2>瀏覽器支援</h2>
    <p>目前主流瀏覽器都支援...</p>
  </section>
</article>

<!-- Landing Page 區段 -->
<main>
  <section id="hero">
    <h1>歡迎來到我們的網站</h1>
    <p>最好的解決方案</p>
    <button>立即開始</button>
  </section>

  <section id="features">
    <h2>產品特色</h2>
    <div>
      <h3>特色 1</h3>
      <p>說明...</p>
    </div>
    <div>
      <h3>特色 2</h3>
      <p>說明...</p>
    </div>
  </section>

  <section id="pricing">
    <h2>價格方案</h2>
    <div>方案內容...</div>
  </section>

  <section id="testimonials">
    <h2>客戶見證</h2>
    <blockquote>很棒的服務！</blockquote>
  </section>

  <section id="contact">
    <h2>聯絡我們</h2>
    <form>...</form>
  </section>
</main>

<!-- 巢狀 section -->
<section>
  <h2>產品系列</h2>

  <section>
    <h3>手機系列</h3>
    <p>最新款手機...</p>
  </section>

  <section>
    <h3>平板系列</h3>
    <p>高效能平板...</p>
  </section>
</section>
```

### ✨ 示範效果

<section style="background: #f8f9fa; padding: 20px; margin-bottom: 15px; border-left: 4px solid #007bff;">
  <h3 style="margin-top: 0;">產品特色</h3>
  <p>我們的產品具有以下優勢：</p>
  <ul>
    <li>高效能</li>
    <li>易於使用</li>
    <li>價格實惠</li>
  </ul>
</section>

<section style="background: #f8f9fa; padding: 20px; border-left: 4px solid #28a745;">
  <h3 style="margin-top: 0;">客戶見證</h3>
  <blockquote style="font-style: italic; color: #6c757d;">
    "這是我用過最好的產品！"
  </blockquote>
</section>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 5+ | ✅ 4+ | ✅ 5+ | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 每個 `<section>` 應該有標題
- ✅ 使用 `aria-label` 或 `aria-labelledby` 提供標籤
- ✅ 適當使用標題層級
- ⚠️ 如果沒有標題，考慮使用 `<div>`

### 使用注意事項

```html
<!-- ❌ 錯誤：沒有標題的 section -->
<section>
  <p>一些內容...</p> <!-- 缺少標題 -->
</section>

<!-- ✅ 正確：有標題或 aria-label -->
<section>
  <h2>標題</h2>
  <p>內容...</p>
</section>

<section aria-label="側邊欄">
  <p>內容...</p>
</section>

<!-- ❌ 錯誤：只為了樣式用 section -->
<section class="wrapper"> <!-- 應該用 div -->
  <p>內容</p>
</section>

<!-- ✅ 正確：用 div 做樣式容器 -->
<div class="wrapper">
  <section>
    <h2>有語意的區段</h2>
  </section>
</div>
```

---

## `<aside>` - 側邊欄/附加內容

### 說明
`<aside>` 代表與主要內容相關但可以獨立的內容，通常顯示為側邊欄。

### 語法
```html
<aside>
  <!-- 附加內容 -->
</aside>
```

### 適用場景

| 場景 | 說明 | 範例 |
|------|------|------|
| 側邊欄 | 頁面側邊欄 | 相關文章、廣告 |
| 引用 | 引述或註解 | 文章內的補充說明 |
| 廣告 | 廣告區塊 | Banner 廣告 |
| 相關連結 | 相關資源 | 推薦閱讀 |
| 作者資訊 | 作者簡介 | 作者卡片 |

### 📌 程式碼範例

```html
<!-- 頁面側邊欄 -->
<main>
  <article>
    <h1>主要文章</h1>
    <p>內容...</p>
  </article>

  <aside>
    <section>
      <h2>相關文章</h2>
      <ul>
        <li><a href="#">文章 1</a></li>
        <li><a href="#">文章 2</a></li>
        <li><a href="#">文章 3</a></li>
      </ul>
    </section>

    <section>
      <h2>分類</h2>
      <ul>
        <li><a href="#">HTML</a></li>
        <li><a href="#">CSS</a></li>
        <li><a href="#">JavaScript</a></li>
      </ul>
    </section>

    <section>
      <h2>標籤雲</h2>
      <a href="#">#HTML5</a>
      <a href="#">#語意化</a>
      <a href="#">#網頁開發</a>
    </section>
  </aside>
</main>

<!-- 文章內的 aside -->
<article>
  <h1>網頁開發指南</h1>

  <p>在開發網頁時...</p>

  <aside>
    <h3>小提示</h3>
    <p>記得要測試跨瀏覽器相容性！</p>
  </aside>

  <p>繼續內容...</p>
</article>

<!-- 作者資訊 -->
<article>
  <h1>文章標題</h1>
  <p>內容...</p>

  <aside>
    <h3>關於作者</h3>
    <img src="avatar.jpg" alt="作者照片">
    <p><strong>張三</strong></p>
    <p>資深網頁開發者，擁有 10 年經驗。</p>
    <a href="/author/zhangsan">更多文章</a>
  </aside>
</article>

<!-- 廣告 -->
<aside aria-label="廣告">
  <p>贊助商廣告</p>
  <img src="ad-banner.jpg" alt="廣告">
</aside>

<!-- 註解/補充說明 -->
<article>
  <p>HTML5 在 2014 年成為 W3C 推薦標準。</p>

  <aside>
    <p><strong>註：</strong>HTML5 的開發從 2004 年就開始了。</p>
  </aside>
</article>
```

### ✨ 示範效果

<div style="display: flex; gap: 20px;">
  <main style="flex: 3; background: #fff; padding: 20px; border: 1px solid #dee2e6;">
    <h3>主要內容區域</h3>
    <p>這裡是網頁的主要內容...</p>
  </main>

  <aside style="flex: 1; background: #f8f9fa; padding: 15px; border: 1px solid #dee2e6;">
    <h4>側邊欄</h4>
    <ul style="padding-left: 20px; margin: 0;">
      <li>相關文章 1</li>
      <li>相關文章 2</li>
      <li>相關文章 3</li>
    </ul>
  </aside>
</div>

<br>

<article style="background: #fff; padding: 20px; border: 1px solid #dee2e6;">
  <p>這是文章的主要段落...</p>

  <aside style="background: #fff3cd; padding: 15px; margin: 15px 0; border-left: 4px solid #ffc107;">
    <strong>提示：</strong> 這是一個補充說明或註解
  </aside>

  <p>文章繼續...</p>
</article>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 5+ | ✅ 4+ | ✅ 5+ | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 使用 `aria-label` 描述 aside 的用途
- ✅ 可以包含標題來說明內容
- ✅ 確保內容與主要內容相關
- ⚠️ 不要在 aside 中放置關鍵內容

### 使用注意事項

```html
<!-- ❌ 錯誤：aside 內容與主內容無關 -->
<article>
  <h1>CSS 教學</h1>
  <aside>
    <h2>JavaScript 入門</h2> <!-- 完全不相關 -->
  </aside>
</article>

<!-- ✅ 正確：相關的補充內容 -->
<article>
  <h1>CSS 教學</h1>
  <aside>
    <h2>相關資源</h2>
    <a href="#">CSS 參考手冊</a>
  </aside>
</article>

<!-- ❌ 錯誤：關鍵導航放在 aside -->
<aside>
  <nav>主選單</nav> <!-- 主選單不應在 aside -->
</aside>

<!-- ✅ 正確：主選單獨立 -->
<nav>主選單</nav>
<aside>
  次要連結
</aside>
```

---

## `<footer>` - 頁尾

### 說明
`<footer>` 代表其最近的區段內容或根元素的頁尾，通常包含作者資訊、版權、相關連結等。

**注意**: 與 `<header>` 類似，可以在多個地方使用。

### 語法
```html
<footer>
  <!-- 頁尾內容 -->
</footer>
```

### 常見用途

| 位置 | 用途 | 範例 |
|------|------|------|
| 頁面底部 | 網站頁尾 | 版權、聯絡資訊、連結 |
| `<article>` 內 | 文章頁尾 | 作者、標籤、分享按鈕 |
| `<section>` 內 | 區段頁尾 | 區段的額外資訊 |

### 📌 程式碼範例

```html
<!-- 網站主頁尾 -->
<footer>
  <div class="footer-content">
    <section>
      <h3>關於我們</h3>
      <p>公司簡介...</p>
    </section>

    <section>
      <h3>快速連結</h3>
      <ul>
        <li><a href="/about">關於</a></li>
        <li><a href="/contact">聯絡</a></li>
        <li><a href="/privacy">隱私政策</a></li>
        <li><a href="/terms">服務條款</a></li>
      </ul>
    </section>

    <section>
      <h3>聯絡資訊</h3>
      <address>
        <p>Email: info@example.com</p>
        <p>電話: (02) 1234-5678</p>
        <p>地址: 台北市信義區...</p>
      </address>
    </section>

    <section>
      <h3>追蹤我們</h3>
      <a href="#">Facebook</a>
      <a href="#">Twitter</a>
      <a href="#">Instagram</a>
    </section>
  </div>

  <div class="copyright">
    <p>&copy; 2026 公司名稱. 版權所有.</p>
  </div>
</footer>

<!-- 文章的頁尾 -->
<article>
  <header>
    <h1>文章標題</h1>
    <p>作者: 張三</p>
  </header>

  <p>文章內容...</p>

  <footer>
    <p>發布於: <time datetime="2026-01-02">2026年1月2日</time></p>
    <p>標籤:
      <a href="/tag/html">#HTML</a>
      <a href="/tag/tutorial">#教學</a>
    </p>
    <p>分享:
      <a href="#">Facebook</a>
      <a href="#">Twitter</a>
    </p>
  </footer>
</article>

<!-- 簡單頁尾 -->
<footer>
  <p>
    &copy; 2026 我的網站 |
    <a href="/privacy">隱私政策</a> |
    <a href="/terms">服務條款</a>
  </p>
</footer>

<!-- 包含多個資訊的頁尾 -->
<footer>
  <nav aria-label="頁尾導航">
    <a href="/about">關於</a>
    <a href="/blog">部落格</a>
    <a href="/careers">職缺</a>
    <a href="/contact">聯絡</a>
  </nav>

  <p>
    訂閱電子報:
    <form>
      <input type="email" placeholder="your@email.com">
      <button type="submit">訂閱</button>
    </form>
  </p>

  <p>&copy; 2026 公司名稱. 版權所有.</p>
</footer>
```

### ✨ 示範效果

<footer style="background: #343a40; color: white; padding: 30px 20px; margin-top: 20px;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-bottom: 20px;">
    <div>
      <h4>關於我們</h4>
      <p style="font-size: 0.9em;">提供優質的網頁開發服務</p>
    </div>
    <div>
      <h4>快速連結</h4>
      <ul style="list-style: none; padding: 0; font-size: 0.9em;">
        <li><a href="#" style="color: #adb5bd;">關於</a></li>
        <li><a href="#" style="color: #adb5bd;">服務</a></li>
        <li><a href="#" style="color: #adb5bd;">聯絡</a></li>
      </ul>
    </div>
    <div>
      <h4>聯絡我們</h4>
      <p style="font-size: 0.9em;">Email: info@example.com</p>
    </div>
  </div>
  <div style="border-top: 1px solid #495057; padding-top: 15px; text-align: center; font-size: 0.9em;">
    &copy; 2026 網站名稱. 版權所有.
  </div>
</footer>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 5+ | ✅ 4+ | ✅ 5+ | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 包含重要的聯絡資訊
- ✅ 提供網站地圖或主要連結
- ✅ 使用 `<address>` 標記聯絡資訊
- ✅ 導航連結使用 `<nav>` 包裹
- ⚠️ 避免在 footer 中放置過多內容

### 使用注意事項

```html
<!-- ❌ 錯誤：footer 內再放 footer -->
<footer>
  <footer>...</footer> <!-- 不應該巢狀 -->
</footer>

<!-- ❌ 錯誤：footer 在 header 內 -->
<header>
  <footer>...</footer> <!-- 不合適 -->
</header>

<!-- ✅ 正確：article 有自己的 footer -->
<article>
  <header>...</header>
  <p>內容...</p>
  <footer>文章資訊</footer>
</article>

<!-- ✅ 正確：頁面主 footer -->
<body>
  <main>...</main>
  <footer>網站頁尾</footer>
</body>
```

---

## `<address>` - 聯絡資訊

### 說明
`<address>` 提供聯絡資訊，通常用於 `<footer>` 或 `<article>` 中。

**注意**: `<address>` 只用於聯絡資訊，不是一般的郵寄地址！

### 語法
```html
<address>
  聯絡資訊
</address>
```

### 📌 程式碼範例

```html
<!-- 網站聯絡資訊 -->
<footer>
  <address>
    <p><strong>聯絡我們</strong></p>
    <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
    <p>電話: <a href="tel:+886212345678">(02) 1234-5678</a></p>
    <p>地址: 台北市信義區信義路五段7號</p>
  </address>
</footer>

<!-- 文章作者聯絡資訊 -->
<article>
  <h1>文章標題</h1>
  <p>內容...</p>

  <footer>
    <address>
      作者: <a href="mailto:author@example.com">張三</a><br>
      網站: <a href="https://example.com">https://example.com</a>
    </address>
  </footer>
</article>

<!-- 公司資訊 -->
<address>
  <strong>ABC 科技有限公司</strong><br>
  台北市信義區信義路五段7號<br>
  統編: 12345678<br>
  客服專線: <a href="tel:0800123456">0800-123-456</a><br>
  Email: <a href="mailto:service@abc.com.tw">service@abc.com.tw</a>
</address>
```

### ✨ 示範效果

<address style="background: #f8f9fa; padding: 15px; border-left: 4px solid #007bff; font-style: normal;">
  <strong>聯絡資訊</strong><br>
  Email: <a href="mailto:info@example.com">info@example.com</a><br>
  電話: (02) 1234-5678<br>
  地址: 台北市信義區信義路五段7號
</address>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 使用 `mailto:` 和 `tel:` 連結
- ✅ 提供完整的聯絡方式
- ✅ 使用清楚的格式
- ⚠️ 預設是斜體，可用 CSS 調整

### 使用注意事項

```html
<!-- ❌ 錯誤：用 address 標記一般地址 -->
<address>
  收件人: 王小明<br>
  台北市中正區...
</address>

<!-- ✅ 正確：只用於聯絡資訊 -->
<address>
  聯絡人: 王小明<br>
  Email: wang@example.com
</address>

<!-- ❌ 錯誤：包含非聯絡資訊 -->
<address>
  公司簡介: 我們是一家...<br> <!-- 不是聯絡資訊 -->
  Email: info@example.com
</address>

<!-- ✅ 正確：只包含聯絡資訊 -->
<address>
  Email: info@example.com<br>
  電話: (02) 1234-5678
</address>
```

---

## `<time>` - 時間/日期

### 說明
`<time>` 標記日期和時間，機器可讀的格式有助於搜尋引擎和其他系統理解。

### 語法
```html
<time datetime="機器可讀格式">人類可讀格式</time>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `datetime` | 機器可讀的日期時間 | ISO 8601 格式 | 否（但建議使用） |

### datetime 格式

| 類型 | 格式 | 範例 |
|------|------|------|
| 日期 | `YYYY-MM-DD` | `2026-01-02` |
| 時間 | `HH:MM` 或 `HH:MM:SS` | `14:30` 或 `14:30:00` |
| 日期時間 | `YYYY-MM-DDTHH:MM` | `2026-01-02T14:30` |
| 時區 | `+HH:MM` 或 `Z` | `2026-01-02T14:30+08:00` |
| 年月 | `YYYY-MM` | `2026-01` |
| 週 | `YYYY-W##` | `2026-W01` |
| 時長 | `PTnHnMnS` | `PT2H30M`（2小時30分） |

### 📌 程式碼範例

```html
<!-- 基本日期 -->
<time datetime="2026-01-02">2026年1月2日</time>

<!-- 日期時間 -->
<time datetime="2026-01-02T14:30">2026年1月2日 下午2:30</time>

<!-- 帶時區 -->
<time datetime="2026-01-02T14:30+08:00">台北時間 2026-01-02 14:30</time>

<!-- 發布日期 -->
<article>
  <h1>文章標題</h1>
  <p>發布於 <time datetime="2026-01-02" pubdate>2026年1月2日</time></p>
</article>

<!-- 時長 -->
<p>烹飪時間: <time datetime="PT30M">30 分鐘</time></p>
<p>影片長度: <time datetime="PT1H30M">1 小時 30 分</time></p>

<!-- 活動日期 -->
<p>
  活動時間:
  <time datetime="2026-03-15">2026年3月15日</time>
  至
  <time datetime="2026-03-17">3月17日</time>
</p>

<!-- 更新時間 -->
<footer>
  <p>最後更新: <time datetime="2026-01-02T10:30">今天 10:30</time></p>
</footer>

<!-- 年份 -->
<p>&copy; <time datetime="2026">2026</time> 公司名稱</p>

<!-- 月份 -->
<p>歸檔: <time datetime="2026-01">2026年1月</time></p>
```

### ✨ 示範效果

<article style="border: 1px solid #dee2e6; padding: 20px;">
  <h3>最新文章</h3>
  <p style="color: #6c757d; font-size: 0.9em;">
    發布於 <time datetime="2026-01-02T14:30" style="font-weight: bold; color: #007bff;">2026年1月2日 14:30</time>
  </p>
  <p>文章摘要...</p>
  <p style="color: #6c757d; font-size: 0.9em;">
    閱讀時間: <time datetime="PT5M" style="font-weight: bold;">5 分鐘</time>
  </p>
</article>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 62+ | ✅ 22+ | ✅ 7+ | ✅ 18+ | ❌ |

### 無障礙建議

- ✅ 總是使用 `datetime` 屬性
- ✅ 提供人類可讀的文字
- ✅ 使用標準的 ISO 8601 格式
- ✅ 對於發布時間使用 `pubdate` (HTML5.1 已移除，但仍常用)

### 使用注意事項

```html
<!-- ❌ 錯誤：datetime 格式錯誤 -->
<time datetime="2026/01/02">2026年1月2日</time>
<time datetime="01-02-2026">2026年1月2日</time>

<!-- ✅ 正確：使用 ISO 8601 格式 -->
<time datetime="2026-01-02">2026年1月2日</time>

<!-- ❌ 錯誤：沒有 datetime，內容格式不標準 -->
<time>昨天</time>

<!-- ✅ 正確：提供 datetime -->
<time datetime="2026-01-01">昨天</time>

<!-- ✅ 正確：相對時間也提供具體 datetime -->
<time datetime="2026-01-02T14:30" title="2026-01-02 14:30">2小時前</time>
```

---

## `<mark>` - 標記/高亮

### 說明
`<mark>` 用於標記或高亮文字，表示參考或標註的目的。

**與 `<strong>` 和 `<em>` 的區別**:
- `<mark>` = 高亮顯示（參考用途）
- `<strong>` = 強調重要性
- `<em>` = 強調語氣

### 語法
```html
<mark>標記的文字</mark>
```

### 適用場景

| 場景 | 說明 | 範例 |
|------|------|------|
| 搜尋結果 | 高亮搜尋關鍵字 | 搜尋結果中的關鍵字 |
| 引用高亮 | 引文中的重點 | 引用文字中的特定部分 |
| 程式碼高亮 | 標記程式碼片段 | 錯誤行或重點行 |
| 變更標記 | 標記文件變更 | 修訂記錄 |

### 📌 程式碼範例

```html
<!-- 搜尋結果高亮 -->
<p>
  搜尋 "HTML5"，找到以下結果：
  <mark>HTML5</mark> 是最新的 <mark>HTML</mark> 標準。
</p>

<!-- 引用中的高亮 -->
<blockquote>
  <p>
    網頁開發有三大支柱：HTML、CSS 和 JavaScript。
    其中 <mark>HTML 負責結構</mark>，CSS 負責樣式，JavaScript 負責互動。
  </p>
</blockquote>

<!-- 文件變更 -->
<p>
  原文: 產品價格為 <del>$999</del> <mark>$799</mark>
</p>

<!-- 程式碼高亮 -->
<pre><code>
function example() {
  <mark>console.log("這行有問題");</mark>
  return true;
}
</code></pre>

<!-- 重要資訊標記 -->
<p>
  請注意：<mark>報名截止日期為 2026 年 1 月 15 日</mark>
</p>

<!-- 測驗答案 -->
<p>
  問題: HTML 代表什麼？<br>
  答案: <mark>HyperText Markup Language</mark>
</p>
```

### ✨ 示範效果

<p>搜尋關鍵字 "語意化"：</p>
<p style="background: white; padding: 15px; border: 1px solid #dee2e6;">
  HTML5 的<mark style="background-color: #fff3cd; padding: 2px 4px;">語意化</mark>標籤讓網頁結構更清晰，有助於 SEO 和無障礙性。使用<mark style="background-color: #fff3cd; padding: 2px 4px;">語意化</mark>標籤是現代網頁開發的最佳實踐。
</p>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ 4+ | ✅ All | ✅ All | ✅ 9+ |

### 無障礙建議

- ✅ 用於參考或標註用途
- ✅ 不要只依賴顏色傳達意義
- ✅ 可以用 CSS 自訂樣式
- ⚠️ 不要用於重要性強調（使用 `<strong>`）

### 使用注意事項

```html
<!-- ❌ 錯誤：用 mark 表示重要性 -->
<p><mark>重要公告</mark></p> <!-- 應該用 strong -->

<!-- ✅ 正確：用 strong 表示重要性 -->
<p><strong>重要公告</strong></p>

<!-- ❌ 錯誤：用 mark 表示語氣強調 -->
<p>我<mark>真的</mark>很喜歡這個產品</p> <!-- 應該用 em -->

<!-- ✅ 正確：用 em 表示語氣 -->
<p>我<em>真的</em>很喜歡這個產品</p>

<!-- ✅ 正確：用 mark 高亮搜尋結果 -->
<p>找到 <mark>HTML5</mark> 相關結果 150 筆</p>

<!-- ✅ 正確：用 mark 標記引用重點 -->
<blockquote>
  <mark>語意化</mark>是 HTML5 的重要特性
</blockquote>
```

---

## 語意化標籤選擇指南

### 決策流程圖

```
是否為頁面頂部的引介內容？
├─ 是 → <header>
└─ 否 ↓

是否為導航連結？
├─ 是 → <nav>
└─ 否 ↓

是否為頁面主要內容？
├─ 是 → <main>
└─ 否 ↓

是否為獨立、可重複使用的內容？
├─ 是 → <article>
└─ 否 ↓

是否為主題性的區段？
├─ 是 → <section>
└─ 否 ↓

是否為附加的相關內容？
├─ 是 → <aside>
└─ 否 ↓

是否為頁尾資訊？
├─ 是 → <footer>
└─ 否 → <div>
```

### 常見問題

#### Q: `<article>` vs `<section>` 如何選擇？

**使用 `<article>`**:
- 內容可以獨立存在
- 可以在 RSS feed 中發布
- 範例：部落格文章、新聞報導、產品卡片

**使用 `<section>`**:
- 內容是文件的主題性區段
- 通常有標題
- 範例：文章的章節、頁面的功能區塊

```html
<!-- article: 獨立的部落格文章 -->
<article>
  <h1>如何學習 HTML</h1>
  <p>完整的教學...</p>
</article>

<!-- section: 文章內的章節 -->
<article>
  <h1>網頁開發指南</h1>
  <section>
    <h2>HTML 基礎</h2>
    <p>...</p>
  </section>
  <section>
    <h2>CSS 樣式</h2>
    <p>...</p>
  </section>
</article>
```

#### Q: `<aside>` 一定要在側邊嗎？

**不一定！** `<aside>` 代表的是內容性質（附加內容），而非視覺位置。

```html
<!-- 可以在側邊 -->
<div class="layout">
  <main>主內容</main>
  <aside class="sidebar">側邊欄</aside>
</div>

<!-- 也可以在文章內部 -->
<article>
  <p>段落...</p>
  <aside>
    <p>註解或補充說明</p>
  </aside>
  <p>繼續...</p>
</article>
```

#### Q: 可以巢狀使用嗎？

大部分語意化標籤可以巢狀，但有規則：

```html
<!-- ✅ 允許的巢狀 -->
<article>
  <header>文章頁首</header>
  <section>
    <header>章節頁首</header>
  </section>
  <footer>文章頁尾</footer>
</article>

<main>
  <article>
    <article>評論</article>
  </article>
</main>

<!-- ❌ 不允許的巢狀 -->
<header>
  <header>...</header> <!-- 不可 -->
</header>

<footer>
  <header>...</header> <!-- 不建議 -->
</footer>

<main>
  <main>...</main> <!-- 不可 -->
</main>
```

---

## 完整網頁布局範例

### 典型部落格頁面

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>我的部落格</title>
</head>
<body>
  <!-- 網站主頁首 -->
  <header>
    <img src="logo.png" alt="部落格 Logo">
    <h1>我的技術部落格</h1>

    <!-- 主導航 -->
    <nav aria-label="主選單">
      <ul>
        <li><a href="/">首頁</a></li>
        <li><a href="/articles">文章</a></li>
        <li><a href="/categories">分類</a></li>
        <li><a href="/about">關於</a></li>
        <li><a href="/contact">聯絡</a></li>
      </ul>
    </nav>
  </header>

  <!-- 主要內容區 -->
  <main>
    <!-- 文章 -->
    <article>
      <!-- 文章頁首 -->
      <header>
        <h1>HTML5 語意化標籤完整指南</h1>

        <!-- 麵包屑 -->
        <nav aria-label="麵包屑">
          <ol>
            <li><a href="/">首頁</a></li>
            <li><a href="/categories/web">網頁開發</a></li>
            <li aria-current="page">HTML5 語意化標籤</li>
          </ol>
        </nav>

        <!-- 元資訊 -->
        <p>
          作者: <a href="/author/zhangsan">張三</a> |
          發布: <time datetime="2026-01-02">2026年1月2日</time> |
          閱讀時間: <time datetime="PT10M">10 分鐘</time>
        </p>

        <p class="summary">
          本文將深入介紹 HTML5 的所有語意化標籤及其使用方法...
        </p>
      </header>

      <!-- 文章目錄 -->
      <nav aria-label="文章目錄">
        <h2>目錄</h2>
        <ol>
          <li><a href="#intro">簡介</a></li>
          <li><a href="#header">Header 標籤</a></li>
          <li><a href="#nav">Nav 標籤</a></li>
          <li><a href="#main">Main 標籤</a></li>
          <li><a href="#conclusion">結論</a></li>
        </ol>
      </nav>

      <!-- 文章內容章節 -->
      <section id="intro">
        <h2>簡介</h2>
        <p>語意化標籤是 HTML5 引入的重要特性...</p>

        <aside>
          <h3>小提示</h3>
          <p>語意化標籤不僅對 SEO 有幫助，也能提升無障礙性。</p>
        </aside>
      </section>

      <section id="header">
        <h2>Header 標籤</h2>
        <p>Header 標籤用於...</p>
      </section>

      <section id="nav">
        <h2>Nav 標籤</h2>
        <p>Nav 標籤代表...</p>
      </section>

      <section id="main">
        <h2>Main 標籤</h2>
        <p>Main 標籤...</p>
      </section>

      <section id="conclusion">
        <h2>結論</h2>
        <p>總結來說，語意化標籤...</p>
      </section>

      <!-- 文章頁尾 -->
      <footer>
        <p>
          標籤:
          <a href="/tag/html5">#HTML5</a>
          <a href="/tag/semantic">#語意化</a>
          <a href="/tag/web-dev">#網頁開發</a>
        </p>

        <p>
          分享文章:
          <a href="#">Facebook</a>
          <a href="#">Twitter</a>
          <a href="#">LinkedIn</a>
        </p>

        <!-- 作者資訊 -->
        <aside>
          <h3>關於作者</h3>
          <img src="avatar.jpg" alt="張三">
          <p><strong>張三</strong></p>
          <p>資深前端工程師，專注於網頁標準和無障礙設計。</p>
          <address>
            Email: <a href="mailto:zhang@example.com">zhang@example.com</a>
          </address>
        </aside>
      </footer>
    </article>

    <!-- 評論區 -->
    <section>
      <h2>評論 (3)</h2>

      <article>
        <header>
          <h3>李四</h3>
          <time datetime="2026-01-02T10:30">2026-01-02 10:30</time>
        </header>
        <p>很棒的文章，學到很多！</p>
      </article>

      <article>
        <header>
          <h3>王五</h3>
          <time datetime="2026-01-02T11:00">2026-01-02 11:00</time>
        </header>
        <p>感謝分享，寫得很清楚。</p>
      </article>

      <article>
        <header>
          <h3>趙六</h3>
          <time datetime="2026-01-02T14:00">2026-01-02 14:00</time>
        </header>
        <p>範例很實用！</p>
      </article>
    </section>
  </main>

  <!-- 側邊欄 -->
  <aside aria-label="側邊欄">
    <!-- 搜尋 -->
    <section>
      <h2>搜尋</h2>
      <form action="/search" method="GET">
        <input type="search" name="q" placeholder="搜尋文章...">
        <button type="submit">搜尋</button>
      </form>
    </section>

    <!-- 分類 -->
    <section>
      <h2>分類</h2>
      <nav aria-label="文章分類">
        <ul>
          <li><a href="/category/html">HTML (25)</a></li>
          <li><a href="/category/css">CSS (18)</a></li>
          <li><a href="/category/javascript">JavaScript (32)</a></li>
          <li><a href="/category/react">React (15)</a></li>
        </ul>
      </nav>
    </section>

    <!-- 最新文章 -->
    <section>
      <h2>最新文章</h2>
      <ul>
        <li>
          <a href="#">CSS Grid 完整指南</a>
          <time datetime="2026-01-01">2026-01-01</time>
        </li>
        <li>
          <a href="#">JavaScript ES2024 新功能</a>
          <time datetime="2025-12-30">2025-12-30</time>
        </li>
        <li>
          <a href="#">React Hooks 深入解析</a>
          <time datetime="2025-12-28">2025-12-28</time>
        </li>
      </ul>
    </section>

    <!-- 標籤雲 -->
    <section>
      <h2>熱門標籤</h2>
      <div>
        <a href="/tag/html5">#HTML5</a>
        <a href="/tag/css3">#CSS3</a>
        <a href="/tag/javascript">#JavaScript</a>
        <a href="/tag/responsive">#響應式</a>
        <a href="/tag/accessibility">#無障礙</a>
      </div>
    </section>

    <!-- 廣告 -->
    <aside aria-label="廣告">
      <p>贊助廣告</p>
      <img src="ad.jpg" alt="廣告內容">
    </aside>
  </aside>

  <!-- 網站頁尾 -->
  <footer>
    <div class="footer-content">
      <!-- 關於 -->
      <section>
        <h3>關於本站</h3>
        <p>專注於分享網頁開發技術和最佳實踐。</p>
      </section>

      <!-- 快速連結 -->
      <section>
        <h3>快速連結</h3>
        <nav aria-label="頁尾導航">
          <ul>
            <li><a href="/about">關於我們</a></li>
            <li><a href="/privacy">隱私政策</a></li>
            <li><a href="/terms">服務條款</a></li>
            <li><a href="/sitemap">網站地圖</a></li>
          </ul>
        </nav>
      </section>

      <!-- 聯絡資訊 -->
      <section>
        <h3>聯絡我們</h3>
        <address>
          Email: <a href="mailto:info@example.com">info@example.com</a><br>
          GitHub: <a href="https://github.com/example">github.com/example</a>
        </address>
      </section>

      <!-- 社群媒體 -->
      <section>
        <h3>追蹤我們</h3>
        <nav aria-label="社群媒體">
          <a href="#">Facebook</a>
          <a href="#">Twitter</a>
          <a href="#">Instagram</a>
          <a href="#">YouTube</a>
        </nav>
      </section>
    </div>

    <!-- 版權資訊 -->
    <div class="copyright">
      <p>
        &copy; <time datetime="2026">2026</time>
        我的技術部落格. 版權所有.
      </p>
    </div>
  </footer>
</body>
</html>
```

### 電商產品頁面

```html
<body>
  <header>
    <h1>網路商店</h1>
    <nav>
      <a href="/">首頁</a>
      <a href="/products">產品</a>
      <a href="/cart">購物車</a>
    </nav>
  </header>

  <main>
    <nav aria-label="麵包屑">
      <ol>
        <li><a href="/">首頁</a></li>
        <li><a href="/category/electronics">電子產品</a></li>
        <li><a href="/category/phones">手機</a></li>
        <li aria-current="page">iPhone 15 Pro</li>
      </ol>
    </nav>

    <article>
      <header>
        <h1>iPhone 15 Pro</h1>
        <p>最新旗艦手機</p>
      </header>

      <section>
        <h2>產品資訊</h2>
        <img src="iphone15.jpg" alt="iPhone 15 Pro 產品圖">

        <p class="price">NT$ 36,900</p>

        <p>庫存狀態: <mark>有貨</mark></p>

        <form>
          <label>顏色:
            <select name="color">
              <option>太空黑</option>
              <option>銀色</option>
              <option>金色</option>
            </select>
          </label>

          <label>容量:
            <select name="storage">
              <option>128GB</option>
              <option>256GB</option>
              <option>512GB</option>
            </select>
          </label>

          <button type="submit">加入購物車</button>
        </form>
      </section>

      <section>
        <h2>產品描述</h2>
        <p>iPhone 15 Pro 搭載...</p>
      </section>

      <section>
        <h2>規格</h2>
        <dl>
          <dt>螢幕</dt>
          <dd>6.1 吋 Super Retina XDR</dd>

          <dt>處理器</dt>
          <dd>A17 Pro 晶片</dd>

          <dt>相機</dt>
          <dd>48MP 主鏡頭</dd>
        </dl>
      </section>
    </article>

    <section>
      <h2>顧客評價</h2>

      <article>
        <header>
          <h3>很棒的手機！</h3>
          <p>評分: ★★★★★</p>
          <p>王小明 | <time datetime="2026-01-01">2026-01-01</time></p>
        </header>
        <p>相機效果非常好...</p>
      </article>
    </section>
  </main>

  <aside>
    <section>
      <h2>相關產品</h2>
      <!-- 產品列表 -->
    </section>

    <section>
      <h2>最近瀏覽</h2>
      <!-- 歷史記錄 -->
    </section>
  </aside>

  <footer>
    <p>&copy; 2026 網路商店</p>
  </footer>
</body>
```

---

## SEO 最佳實踐

### 1. 使用正確的標題層級

```html
<!-- ❌ 錯誤：跳過層級 -->
<h1>網站標題</h1>
<h3>直接跳到 h3</h3> <!-- 缺少 h2 -->

<!-- ✅ 正確：依序使用 -->
<h1>網站標題</h1>
<h2>主要章節</h2>
<h3>次要章節</h3>
```

### 2. 每頁只有一個 `<h1>`

```html
<!-- ❌ 錯誤：多個 h1 -->
<h1>網站名稱</h1>
<h1>頁面標題</h1>

<!-- ✅ 正確：只有一個 h1 -->
<header>
  <p>網站名稱</p> <!-- 或用 CSS 放大 -->
</header>
<main>
  <h1>頁面標題</h1>
</main>
```

### 3. 使用語意化標籤建立清晰結構

```html
<!-- ✅ 搜尋引擎能理解的結構 -->
<header>
  <nav>導航</nav>
</header>
<main>
  <article>
    <header>
      <h1>文章標題</h1>
      <time>日期</time>
    </header>
    <section>內容</section>
  </article>
</main>
<footer>頁尾</footer>
```

### 4. 提供充分的元資訊

```html
<article>
  <header>
    <h1>文章標題</h1>
    <p>作者: <a href="/author/name">姓名</a></p>
    <time datetime="2026-01-02" pubdate>2026-01-02</time>
    <p>分類: <a href="/category/tech">科技</a></p>
  </header>
  <p>內容...</p>
  <footer>
    <p>標籤: <a href="/tag/html">#HTML</a></p>
  </footer>
</article>
```

### 5. 使用 Schema.org 微資料 (進階)

```html
<article itemscope itemtype="https://schema.org/Article">
  <header>
    <h1 itemprop="headline">文章標題</h1>
    <p>作者: <span itemprop="author">張三</span></p>
    <time itemprop="datePublished" datetime="2026-01-02">2026-01-02</time>
  </header>
  <div itemprop="articleBody">
    <p>文章內容...</p>
  </div>
</article>
```

---

## 最佳實踐總結

### ✅ 必須做的事

1. **正確使用語意化標籤**
   - 根據內容性質選擇適當的標籤
   - 不要濫用 `<div>` 和 `<span>`
   - 理解每個標籤的真正含義

2. **建立清晰的文件結構**
   - 使用 `<header>`, `<main>`, `<footer>` 建立基本架構
   - 用 `<nav>` 標記主要導航
   - 用 `<article>` 和 `<section>` 組織內容

3. **標題層級要正確**
   - 每頁只有一個 `<h1>`
   - 不要跳過層級
   - 每個 `<section>` 和 `<article>` 應該有標題

4. **提升無障礙性**
   - 使用 `aria-label` 和 `aria-labelledby` 區分重複的標籤
   - 使用 `aria-current` 標示當前頁面
   - 確保鍵盤可導航

5. **SEO 優化**
   - 提供豐富的元資訊
   - 使用 `<time>` 標記日期
   - 使用 `<address>` 標記聯絡資訊
   - 考慮使用 Schema.org 微資料

### ❌ 避免的事

1. **不當使用語意化標籤**
   - ❌ 只為了樣式使用語意化標籤
   - ❌ 用錯標籤（如用 `<article>` 包裹導航）
   - ❌ 過度使用（如所有 `<div>` 都改成 `<section>`）

2. **結構問題**
   - ❌ 一個頁面多個 `<main>`
   - ❌ 不當的標籤巢狀
   - ❌ 缺少必要的包裹元素

3. **無障礙問題**
   - ❌ 缺少標題
   - ❌ 沒有區分多個相同類型的標籤
   - ❌ 標題層級跳躍

4. **SEO 問題**
   - ❌ 多個 `<h1>`
   - ❌ 缺少元資訊
   - ❌ 使用 `<div>` 堆砌而非語意化標籤

### 🎯 進階優化

1. **微資料整合**
   - 使用 Schema.org 標記
   - 提供結構化資料
   - 提升搜尋結果呈現

2. **進階無障礙**
   - 實作「跳到主要內容」連結
   - 使用 ARIA landmark roles (補充)
   - 確保完整的鍵盤導航

3. **效能考量**
   - 語意化標籤本身不影響效能
   - 但清晰的結構有助於 CSS 和 JS 最佳化

4. **回應式設計**
   - 語意化標籤與 RWD 完美搭配
   - 使用 Flexbox/Grid 配合語意化標籤
   - 行動優先的結構設計

---

**記住**: 語意化不是為了瀏覽器（所有標籤在瀏覽器看來都一樣），而是為了：
1. **人類** - 開發者更容易閱讀和維護
2. **搜尋引擎** - 更好地理解內容和結構
3. **輔助技術** - 螢幕閱讀器能更好地導航
4. **未來** - 符合網頁標準，更好的相容性

---

[⬆️ 回到頂部](#語意化標籤-semantic-elements) | [📑 回索引頁](index.md)
