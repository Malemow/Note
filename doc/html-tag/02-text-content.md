# 文字內容標籤

> 用於文字排版與內容呈現的 HTML 標籤

## 📑 目錄

### 標題與段落
- [\<h1\> - \<h6\>](#h1---h6-標題)
- [\<p\>](#p-段落)

### 容器元素
- [\<div\>](#div-區塊容器)
- [\<span\>](#span-行內容器)

### 換行與分隔
- [\<br\>](#br-換行)
- [\<hr\>](#hr-水平線)

### 文字強調
- [\<strong\>](#strong-強調重要性)
- [\<em\>](#em-強調語氣)
- [\<b\>](#b-粗體)
- [\<i\>](#i-斜體)
- [\<u\>](#u-底線)
- [\<s\>](#s-刪除線)
- [\<mark\>](#mark-標記高亮)
- [\<small\>](#small-小字)

### 上下標
- [\<sub\>](#sub-下標)
- [\<sup\>](#sup-上標)

### 程式碼相關
- [\<code\>](#code-程式碼)
- [\<pre\>](#pre-預格式化文字)
- [\<kbd\>](#kbd-鍵盤輸入)
- [\<samp\>](#samp-範例輸出)
- [\<var\>](#var-變數)

### 引用與縮寫
- [\<abbr\>](#abbr-縮寫)
- [\<cite\>](#cite-引用來源)
- [\<q\>](#q-行內引用)
- [\<blockquote\>](#blockquote-區塊引用)

---

## \<h1\> - \<h6\> 標題

### 說明
標題標籤共有六個層級（`<h1>` 到 `<h6>`），用於定義文件的標題結構。`<h1>` 是最高層級（最重要），`<h6>` 是最低層級。

### 語法
```html
<h1>最重要的標題</h1>
<h2>次要標題</h2>
<h3>第三級標題</h3>
<h4>第四級標題</h4>
<h5>第五級標題</h5>
<h6>第六級標題</h6>
```

### 全域屬性
支援所有 HTML 全域屬性（`id`, `class`, `style` 等）

### 📌 程式碼範例

#### 基本使用
```html
<h1>網站主標題</h1>
<h2>章節標題</h2>
<h3>子章節標題</h3>
```

#### 完整文章結構
```html
<article>
    <h1>HTML 完整教學指南</h1>

    <section>
        <h2>第一章：基礎概念</h2>
        <h3>1.1 什麼是 HTML</h3>
        <p>HTML 是...</p>

        <h3>1.2 HTML 的歷史</h3>
        <p>HTML 起源於...</p>
    </section>

    <section>
        <h2>第二章：標籤介紹</h2>
        <h3>2.1 基本結構標籤</h3>
        <h4>2.1.1 DOCTYPE 宣告</h4>
        <p>DOCTYPE 的用途是...</p>
    </section>
</article>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<h1>這是 h1 標題</h1>
<h2>這是 h2 標題</h2>
<h3>這是 h3 標題</h3>
<h4>這是 h4 標題</h4>
<h5>這是 h5 標題</h5>
<h6>這是 h6 標題</h6>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式（可能因瀏覽器而異）
| 標籤 | 字體大小 | 粗細 | 上下邊距 |
|------|---------|------|---------|
| `<h1>` | 2em (32px) | bold | 0.67em |
| `<h2>` | 1.5em (24px) | bold | 0.83em |
| `<h3>` | 1.17em (18.72px) | bold | 1em |
| `<h4>` | 1em (16px) | bold | 1.33em |
| `<h5>` | 0.83em (13.28px) | bold | 1.67em |
| `<h6>` | 0.67em (10.72px) | bold | 2.33em |

### SEO 最佳實踐
- ✅ 每個頁面只使用一個 `<h1>`
- ✅ 按照層級順序使用（不要跳過層級）
- ✅ 標題要描述性強且包含關鍵字
- ❌ 不要僅為了視覺效果選擇標題層級（應使用 CSS）

### 無障礙建議
- ✅ 標題要有邏輯層級結構
- ✅ 螢幕閱讀器會使用標題導航
- ✅ 不要用標題僅為了文字變大（使用 CSS）
- ✅ 確保標題文字有意義

### 使用注意事項
```html
<!-- ❌ 錯誤：跳過層級 -->
<h1>主標題</h1>
<h3>直接跳到 h3</h3>

<!-- ❌ 錯誤：多個 h1 -->
<h1>標題 1</h1>
<h1>標題 2</h1>

<!-- ❌ 錯誤：為了樣式使用標題 -->
<h5>我想要小字</h5>

<!-- ✅ 正確：按層級使用 -->
<h1>主標題</h1>
<h2>副標題</h2>
<h3>子標題</h3>

<!-- ✅ 正確：用 CSS 調整樣式 -->
<h2 style="font-size: 14px;">樣式客製化的 h2</h2>
```

---

## \<p\> 段落

### 說明
`<p>` (paragraph) 標籤定義一個文字段落，是最常用的文字容器之一。瀏覽器會自動在段落前後添加空白。

### 語法
```html
<p>這是一個段落。</p>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 基本段落
```html
<p>這是第一段文字內容。</p>
<p>這是第二段文字內容。</p>
```

#### 段落內的行內元素
```html
<p>
    這段文字包含 <strong>粗體</strong>、
    <em>斜體</em>、
    <a href="#">連結</a> 和
    <mark>高亮</mark> 等元素。
</p>
```

#### 長段落範例
```html
<article>
    <h2>文章標題</h2>
    <p>
        這是文章的第一段。段落標籤會自動在前後加上適當的間距，
        讓內容更易於閱讀。段落內可以包含各種行內元素。
    </p>
    <p>
        這是第二段。每個段落應該包含一個完整的想法或概念。
        過長的段落會降低可讀性，建議適當分段。
    </p>
</article>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是一個普通的段落文字。</p>
<p>這是另一個段落，瀏覽器會自動在段落之間添加間距。</p>
<p>段落內可以包含 <strong>粗體</strong>、<em>斜體</em> 和 <a href="#">連結</a>。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
p {
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0;
    margin-inline-end: 0;
}
```

### 使用注意事項
```html
<!-- ❌ 錯誤：巢狀段落 -->
<p>外層段落 <p>內層段落</p> 繼續外層</p>

<!-- ❌ 錯誤：在段落內放區塊元素 -->
<p>
    <div>這是錯誤的</div>
</p>

<!-- ✅ 正確：獨立段落 -->
<p>第一段</p>
<p>第二段</p>

<!-- ✅ 正確：段落內只放行內元素 -->
<p>
    文字 <span>行內元素</span> <strong>粗體</strong>
</p>
```

---

## \<div\> 區塊容器

### 說明
`<div>` (division) 是通用的區塊級容器，用於將內容分組。它本身沒有語意意義，主要用於布局和樣式設定。

### 語法
```html
<div>
    <!-- 內容 -->
</div>
```

### 全域屬性
支援所有 HTML 全域屬性，常配合 `class` 和 `id` 使用

### 📌 程式碼範例

#### 基本布局
```html
<div class="container">
    <div class="header">
        <h1>網站標題</h1>
    </div>

    <div class="content">
        <p>主要內容</p>
    </div>

    <div class="footer">
        <p>頁尾資訊</p>
    </div>
</div>
```

#### 卡片組件
```html
<div class="card">
    <div class="card-header">
        <h3>卡片標題</h3>
    </div>
    <div class="card-body">
        <p>卡片內容文字...</p>
    </div>
    <div class="card-footer">
        <button>了解更多</button>
    </div>
</div>
```

#### 網格系統
```html
<div class="row">
    <div class="col-4">
        <p>第一列</p>
    </div>
    <div class="col-4">
        <p>第二列</p>
    </div>
    <div class="col-4">
        <p>第三列</p>
    </div>
</div>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<div style="border: 1px solid #ccc; padding: 10px; margin: 10px 0;">
    這是一個 div 容器
    <div style="background-color: #f0f0f0; padding: 10px; margin: 5px 0;">
        巢狀的 div 元素
    </div>
</div>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
div {
    display: block;
}
```

### 語意化替代方案
在 HTML5 中，應優先使用語意化標籤：

| 用途 | 用 div | 改用語意化標籤 |
|------|--------|---------------|
| 頁首 | `<div class="header">` | `<header>` ✅ |
| 導航 | `<div class="nav">` | `<nav>` ✅ |
| 主內容 | `<div class="main">` | `<main>` ✅ |
| 側邊欄 | `<div class="sidebar">` | `<aside>` ✅ |
| 文章 | `<div class="article">` | `<article>` ✅ |
| 章節 | `<div class="section">` | `<section>` ✅ |
| 頁尾 | `<div class="footer">` | `<footer>` ✅ |

### 使用注意事項
```html
<!-- ❌ 過度使用 div -->
<div>
    <div>
        <div>
            <div>只是一段文字</div>
        </div>
    </div>
</div>

<!-- ❌ 應該用語意化標籤的地方用 div -->
<div class="header">
    <div class="nav">...</div>
</div>

<!-- ✅ 適當使用 div（純布局用途） -->
<div class="container">
    <header>...</header>
    <main>...</main>
</div>

<!-- ✅ 優先使用語意化標籤 -->
<header>
    <nav>...</nav>
</header>
```

---

## \<span\> 行內容器

### 說明
`<span>` 是通用的行內容器，用於為文字的一部分設定樣式或加上特定屬性。與 `<div>` 類似，它本身沒有語意意義。

### 語法
```html
<span>文字內容</span>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 文字樣式
```html
<p>
    這段文字中有
    <span style="color: red;">紅色</span>、
    <span style="font-weight: bold;">粗體</span> 和
    <span class="highlight">特殊樣式</span>
    的部分。
</p>
```

#### 多語言標記
```html
<p>
    我喜歡說
    <span lang="en">Hello</span>、
    <span lang="ja">こんにちは</span> 和
    <span lang="ko">안녕하세요</span>。
</p>
```

#### 資料屬性
```html
<p>
    產品價格：
    <span class="price" data-currency="TWD" data-amount="1000">
        NT$ 1,000
    </span>
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>
    這是普通文字，
    <span style="color: blue;">這裡是藍色文字</span>，
    <span style="background-color: yellow;">這裡有黃色背景</span>。
</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
span {
    display: inline;
}
```

### 與其他行內標籤的對比

| 標籤 | 用途 | 語意 |
|------|------|------|
| `<span>` | 通用容器 | 無語意 |
| `<strong>` | 強調重要性 | 有語意 ✅ |
| `<em>` | 強調語氣 | 有語意 ✅ |
| `<mark>` | 標記高亮 | 有語意 ✅ |
| `<code>` | 程式碼 | 有語意 ✅ |

### 使用注意事項
```html
<!-- ❌ 應該用語意化標籤的地方用 span -->
<p>這很<span class="important">重要</span>！</p>

<!-- ✅ 使用語意化標籤 -->
<p>這很<strong>重要</strong>！</p>

<!-- ❌ 不必要的巢狀 -->
<span><span><span>文字</span></span></span>

<!-- ✅ 僅在需要時使用 -->
<p>普通文字 <span class="tooltip" data-tip="提示">帶提示的文字</span></p>
```

---

## \<br\> 換行

### 說明
`<br>` (line break) 標籤用於插入換行符號，不會產生新段落。這是一個空元素（void element），不需要結束標籤。

### 語法
```html
<!-- HTML5 -->
<br>

<!-- XHTML -->
<br />
```

### 無屬性
不支援任何特定屬性，僅支援全域屬性

### 📌 程式碼範例

#### 基本換行
```html
<p>
    第一行文字<br>
    第二行文字<br>
    第三行文字
</p>
```

#### 地址格式
```html
<address>
    張小明<br>
    台北市信義區信義路五段7號<br>
    電話：02-1234-5678
</address>
```

#### 詩歌排版
```html
<p>
    床前明月光，<br>
    疑是地上霜。<br>
    舉頭望明月，<br>
    低頭思故鄉。
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>
這是第一行<br>
這是第二行<br>
這是第三行
</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項
```html
<!-- ❌ 錯誤：用多個 br 製造空白 -->
<p>段落一</p>
<br><br><br>
<p>段落二</p>

<!-- ✅ 正確：用 CSS margin 控制間距 -->
<p>段落一</p>
<p style="margin-top: 2em;">段落二</p>

<!-- ❌ 錯誤：用 br 分隔項目 -->
<p>
    項目 1<br>
    項目 2<br>
    項目 3
</p>

<!-- ✅ 正確：使用列表 -->
<ul>
    <li>項目 1</li>
    <li>項目 2</li>
    <li>項目 3</li>
</ul>

<!-- ✅ 正確：適合用 br 的場景 -->
<p>
    公司名稱<br>
    地址第一行<br>
    地址第二行
</p>
```

### 無障礙建議
- ⚠️ 螢幕閱讀器可能會朗讀每個 `<br>`
- ✅ 避免連續使用多個 `<br>` 製造空白
- ✅ 優先考慮使用 CSS 排版

---

## \<hr\> 水平線

### 說明
`<hr>` (horizontal rule) 標籤表示主題轉換或內容分隔，在視覺上顯示為水平線。HTML5 中它具有語意意義，不僅僅是裝飾性元素。

### 語法
```html
<!-- HTML5 -->
<hr>

<!-- XHTML -->
<hr />
```

### 全域屬性
支援所有 HTML 全域屬性

### 已廢棄屬性
| 屬性 | 說明 | 替代方案 |
|------|------|---------|
| `size` | 線條粗細 | CSS `height` |
| `width` | 線條寬度 | CSS `width` |
| `align` | 對齊方式 | CSS `margin` |
| `color` | 線條顏色 | CSS `border-color` |
| `noshade` | 實心線條 | CSS `border-style` |

### 📌 程式碼範例

#### 基本使用
```html
<p>第一段內容</p>
<hr>
<p>第二段內容（不同主題）</p>
```

#### 文章分隔
```html
<article>
    <h2>第一個主題</h2>
    <p>這是第一個主題的內容...</p>

    <hr>

    <h2>第二個主題</h2>
    <p>這是第二個主題的內容...</p>
</article>
```

#### CSS 樣式化
```html
<!-- 虛線樣式 -->
<hr style="border-style: dashed;">

<!-- 自訂顏色和粗細 -->
<hr style="border: 2px solid #333;">

<!-- 短線條 -->
<hr style="width: 50%; margin: 20px auto; border: 1px solid #ccc;">
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>第一段內容</p>
<hr>
<p>第二段內容</p>

<p>自訂樣式的分隔線：</p>
<hr style="border: 2px dashed #999;">

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
hr {
    display: block;
    unicode-bidi: isolate;
    margin-block-start: 0.5em;
    margin-block-end: 0.5em;
    margin-inline-start: auto;
    margin-inline-end: auto;
    overflow: hidden;
    border-style: inset;
    border-width: 1px;
}
```

### 使用注意事項
```html
<!-- ❌ 錯誤：僅作為裝飾使用 -->
<div>
    <hr>
    <p>這只是裝飾</p>
    <hr>
</div>

<!-- ✅ 正確：表示主題轉換 -->
<section>
    <h2>關於我們</h2>
    <p>公司介紹...</p>
</section>
<hr>
<section>
    <h2>聯絡方式</h2>
    <p>聯絡資訊...</p>
</section>

<!-- ❌ 不要使用廢棄屬性 -->
<hr width="50%" size="3" color="red">

<!-- ✅ 使用 CSS -->
<hr style="width: 50%; height: 3px; border-color: red;">
```

---

## \<strong\> 強調重要性

### 說明
`<strong>` 標籤表示內容具有強烈的重要性、嚴重性或緊急性。瀏覽器通常以粗體顯示，但重點是語意而非樣式。

### 語法
```html
<strong>重要內容</strong>
```

### 全域屬性
支援所有 HTML 全域屬性

### 與 \<b\> 的區別

| 標籤 | 語意 | 用途 | 螢幕閱讀器 |
|------|------|------|-----------|
| `<strong>` | 強調重要性 | 語意化強調 | 會強調語氣 ✅ |
| `<b>` | 無語意 | 純視覺粗體 | 不強調 |

### 📌 程式碼範例

#### 基本使用
```html
<p><strong>警告：</strong>此操作無法復原！</p>
<p>今天的天氣<strong>非常炎熱</strong>，請多補充水分。</p>
```

#### 多層強調
```html
<p>
    <strong>重要通知：</strong>
    系統將於明天維護，
    <strong>請務必備份您的資料</strong>。
</p>
```

#### 巢狀強調
```html
<p>
    <strong>
        這整段都很重要，
        <em>而且這部分更需要注意</em>。
    </strong>
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是普通文字，<strong>這是重要的內容</strong>，繼續普通文字。</p>
<p><strong>警告：</strong>請勿在密閉空間使用。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
strong {
    font-weight: bold;
}
```

### 使用場景
✅ **適合使用 `<strong>`：**
- 警告訊息
- 重要聲明
- 關鍵資訊
- 強調重要性

❌ **不適合使用 `<strong>`：**
- 僅為視覺效果的粗體（使用 `<b>` 或 CSS）
- 標題（使用 `<h1>-<h6>`）
- 強調語氣（使用 `<em>`）

### 無障礙建議
- ✅ 螢幕閱讀器會以更強的語氣朗讀 `<strong>` 內容
- ✅ 不要過度使用，否則會失去強調效果
- ✅ 適當搭配 `<em>` 使用

### 使用注意事項
```html
<!-- ❌ 錯誤：僅為樣式使用 -->
<strong>這個標題</strong>

<!-- ✅ 正確：表示重要性 -->
<p><strong>注意：</strong>此商品即將售罄。</p>

<!-- ❌ 過度使用 -->
<p>
    <strong>這段</strong>
    <strong>文字</strong>
    <strong>全是</strong>
    <strong>strong</strong>
</p>

<!-- ✅ 適當使用 -->
<p>
    這個產品有 <strong>30 天無條件退貨</strong> 保證。
</p>
```

---

## \<em\> 強調語氣

### 說明
`<em>` (emphasis) 標籤表示強調語氣或重音。瀏覽器通常以斜體顯示，但重點是語意而非樣式。

### 語法
```html
<em>強調內容</em>
```

### 全域屬性
支援所有 HTML 全域屬性

### 與 \<i\> 的區別

| 標籤 | 語意 | 用途 | 螢幕閱讀器 |
|------|------|------|-----------|
| `<em>` | 強調語氣 | 語意化強調 | 會改變語調 ✅ |
| `<i>` | 無語意 | 純視覺斜體 | 不改變語調 |

### 📌 程式碼範例

#### 基本使用
```html
<p>我<em>真的</em>很喜歡這個產品。</p>
<p>請<em>小心</em>使用。</p>
```

#### 不同語氣的強調
```html
<p>我<em>沒有</em>拿你的錢！</p>
<p>我沒有拿<em>你的</em>錢！</p>
<p>我沒有拿你的<em>錢</em>！</p>
```

#### 與 strong 搭配使用
```html
<p>
    <strong>重要：</strong>
    這個步驟<em>絕對不能</em>省略。
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是普通文字，<em>這部分有強調語氣</em>，繼續普通文字。</p>
<p>我<em>真的</em>不知道這件事。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
em {
    font-style: italic;
}
```

### 使用場景
✅ **適合使用 `<em>`：**
- 語氣強調
- 口語重音
- 對比強調

❌ **不適合使用 `<em>`：**
- 書籍、電影名稱（使用 `<cite>`）
- 技術術語（使用 `<i>` 或 `<dfn>`）
- 僅為視覺效果的斜體（使用 `<i>` 或 CSS）

### 無障礙建議
- ✅ 螢幕閱讀器會改變語調朗讀 `<em>` 內容
- ✅ 用於傳達口語化的強調
- ✅ 搭配標點符號使用效果更好

### 使用注意事項
```html
<!-- ❌ 錯誤：用於書籍名稱 -->
<p>我最近在看<em>哈利波特</em>。</p>

<!-- ✅ 正確：使用 cite -->
<p>我最近在看<cite>哈利波特</cite>。</p>

<!-- ❌ 僅為樣式 -->
<em>這是標題</em>

<!-- ✅ 正確：語氣強調 -->
<p>你<em>確定</em>要這麼做嗎？</p>
```

---

## \<b\> 粗體

### 說明
`<b>` (bold) 標籤用於將文字顯示為粗體，但不傳達額外的語意重要性。當需要粗體樣式但沒有特殊強調意義時使用。

### 語法
```html
<b>粗體文字</b>
```

### 全域屬性
支援所有 HTML 全域屬性

### 何時使用 \<b\>

| 場景 | 使用標籤 | 原因 |
|------|---------|------|
| 關鍵字高亮 | `<b>` | 無語意意義的粗體 |
| 產品名稱 | `<b>` | 視覺區分 |
| 重要通知 | `<strong>` | 有語意重要性 |
| 警告訊息 | `<strong>` | 有語意重要性 |

### 📌 程式碼範例

#### 基本使用
```html
<p>
    在這篇文章中，
    <b>關鍵字</b>
    會以粗體顯示。
</p>
```

#### 摘要開頭
```html
<article>
    <p>
        <b>摘要：</b>
        這篇文章討論 HTML 標籤的使用方法...
    </p>
</article>
```

#### 產品清單
```html
<ul>
    <li><b>產品名稱：</b>無線滑鼠</li>
    <li><b>價格：</b>NT$ 500</li>
    <li><b>庫存：</b>充足</li>
</ul>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是普通文字，<b>這是粗體文字</b>，繼續普通文字。</p>
<p><b>注意：</b>這只是視覺上的粗體，沒有語意強調。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
b {
    font-weight: bold;
}
```

### \<b\> vs \<strong\> 選擇指南

```html
<!-- 使用 <b>：僅需視覺粗體 -->
<p><b>規格：</b>15.6 吋螢幕</p>

<!-- 使用 <strong>：內容很重要 -->
<p><strong>警告：</strong>請勿接觸高溫表面</p>

<!-- 使用 <b>：列表標籤 -->
<ul>
    <li><b>顏色：</b>黑色</li>
</ul>

<!-- 使用 <strong>：關鍵資訊 -->
<p>此優惠<strong>僅限今天</strong>！</p>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：用 b 表示重要性 -->
<p><b>緊急通知</b>：系統即將關閉</p>

<!-- ✅ 正確：用 strong -->
<p><strong>緊急通知：</strong>系統即將關閉</p>

<!-- ✅ 正確：用 b 做視覺標記 -->
<p><b>作者：</b>張小明</p>
```

---

## \<i\> 斜體

### 說明
`<i>` (italic) 標籤用於將文字顯示為斜體，表示與正常文字在語氣、語態或品質上有所不同，但不強調重要性。

### 語法
```html
<i>斜體文字</i>
```

### 全域屬性
支援所有 HTML 全域屬性

### 適用場景

| 場景 | 使用標籤 | 範例 |
|------|---------|------|
| 外文詞彙 | `<i>` | `<i>café</i>` |
| 技術術語 | `<i>` | `<i>Homo sapiens</i>` |
| 思想內容 | `<i>` | `<i>他心想：完了</i>` |
| 船名、書名（西方） | `<i>` | `<i>Titanic</i>` |
| 強調語氣 | `<em>` | `你<em>確定</em>嗎？` |
| 書籍、作品名 | `<cite>` | `<cite>哈利波特</cite>` |

### 📌 程式碼範例

#### 外文詞彙
```html
<p>
    我們去了一家很棒的<i lang="fr">café</i>。
</p>
```

#### 技術術語
```html
<p>
    人類的學名是<i>Homo sapiens</i>。
</p>
```

#### 思想或內心獨白
```html
<p>
    他看著帳單，<i>這也太貴了吧！</i>
</p>
```

#### 圖標字體（Font Icons）
```html
<i class="fa fa-home" aria-hidden="true"></i>
<span class="sr-only">首頁</span>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是普通文字，<i>這是斜體文字</i>，繼續普通文字。</p>
<p>學名：<i>Felis catus</i>（貓）</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
i {
    font-style: italic;
}
```

### 標籤選擇指南

```html
<!-- 使用 <i>：外文詞彙 -->
<p>我點了<i lang="it">cappuccino</i>。</p>

<!-- 使用 <em>：強調語氣 -->
<p>我<em>真的</em>不知道。</p>

<!-- 使用 <cite>：作品名稱 -->
<p>我讀過<cite>紅樓夢</cite>。</p>

<!-- 使用 <dfn>：術語定義 -->
<p><dfn>HTML</dfn> 是超文本標記語言。</p>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：用 i 表示強調 -->
<p>這<i>非常</i>重要！</p>

<!-- ✅ 正確：用 em -->
<p>這<em>非常</em>重要！</p>

<!-- ✅ 正確：用 i 標記外文 -->
<p>這是法文的<i lang="fr">bonjour</i>。</p>
```

---

## \<u\> 底線

### 說明
`<u>` (underline) 標籤為文字添加底線，在 HTML5 中重新定義為表示「非文本註釋」，如拼寫錯誤標記或專有名詞。

### 語法
```html
<u>底線文字</u>
```

### ⚠️ 使用警告
- 底線容易與超連結混淆
- 建議使用 CSS `text-decoration: underline` 代替
- 僅在有語意必要時使用

### 📌 程式碼範例

#### 拼寫錯誤標記
```html
<p>
    他寫道：「我<u class="spelling-error">必需</u>完成作業。」
    （正確應為「必須」）
</p>
```

#### 專有名詞（中文）
```html
<p>
    古代典籍中的<u>詩經</u>是重要文獻。
</p>
```

#### CSS 樣式化（推薦）
```html
<p>
    使用 CSS 更靈活：
    <span style="text-decoration: underline;">底線文字</span>
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是普通文字，<u>這是有底線的文字</u>，繼續普通文字。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
u {
    text-decoration: underline;
}
```

### 替代方案

| 用途 | 不要用 | 應該用 |
|------|--------|--------|
| 超連結 | `<u>` | `<a>` ✅ |
| 強調 | `<u>` | `<em>` 或 `<strong>` ✅ |
| 樣式底線 | `<u>` | CSS `text-decoration` ✅ |
| 拼寫錯誤 | - | `<u class="spelling">` ✅ |

### 使用注意事項
```html
<!-- ❌ 錯誤：模擬連結 -->
<u>點擊這裡</u>

<!-- ✅ 正確：使用 a 標籤 -->
<a href="#">點擊這裡</a>

<!-- ❌ 錯誤：純裝飾 -->
<u>重要文字</u>

<!-- ✅ 正確：使用語意標籤或 CSS -->
<strong>重要文字</strong>
<span style="text-decoration: underline;">裝飾文字</span>

<!-- ✅ 適當使用：標記錯誤 -->
<p>他寫的是<u class="typo">seperator</u>（正確：separator）</p>
```

---

## \<s\> 刪除線

### 說明
`<s>` (strikethrough) 標籤表示內容不再準確或不再相關，在視覺上顯示為刪除線。

### 語法
```html
<s>刪除的內容</s>
```

### 與 \<del\> 的區別

| 標籤 | 語意 | 用途 |
|------|------|------|
| `<s>` | 不再準確或相關 | 價格變動、過時資訊 |
| `<del>` | 文件修訂中刪除 | 編輯歷史、版本對比 |

### 📌 程式碼範例

#### 價格變動
```html
<p>
    原價：<s>NT$ 1,000</s> 特價：NT$ 800
</p>
```

#### 售完商品
```html
<ul>
    <li>藍色 - 有貨</li>
    <li><s>紅色 - 售完</s></li>
    <li>綠色 - 有貨</li>
</ul>
```

#### 更新資訊
```html
<p>
    活動日期：<s>2025年12月31日</s> 2026年1月15日
    （已延期）
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>原價：<s>NT$ 500</s> 特價：NT$ 350</p>
<p><s>此商品已停售</s></p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
s {
    text-decoration: line-through;
}
```

### 使用注意事項
```html
<!-- ✅ 正確：價格變動 -->
<p><s>$100</s> $80</p>

<!-- ✅ 正確：過時資訊 -->
<p><s>此優惠已過期</s></p>

<!-- ❌ 錯誤：文件編輯歷史 -->
<p>我喜歡<s>蘋果</s>橘子。</p>

<!-- ✅ 正確：使用 del -->
<p>我喜歡<del>蘋果</del><ins>橘子</ins>。</p>
```

---

## \<mark\> 標記高亮

### 說明
`<mark>` 標籤用於標記或高亮文字，表示該內容與當前上下文相關或需要注意。瀏覽器通常以黃色背景顯示。

### 語法
```html
<mark>標記文字</mark>
```

### 全域屬性
支援所有 HTML 全域屬性

### 使用場景
- 搜尋結果中的關鍵字
- 引用中的特別關注部分
- 程式碼中的變更部分

### 📌 程式碼範例

#### 搜尋結果高亮
```html
<p>
    搜尋「<mark>HTML</mark>」的結果：
    <mark>HTML</mark> 是超文本標記語言...
</p>
```

#### 重點標記
```html
<blockquote>
    這段引文中，
    <mark>這部分特別重要</mark>，
    需要特別注意。
</blockquote>
```

#### 對比標記
```html
<p>
    2025 年銷售額：<mark>120 萬</mark>（成長 20%）<br>
    2024 年銷售額：100 萬
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是普通文字，<mark>這部分被標記</mark>，繼續普通文字。</p>
<p>搜尋結果：找到關鍵字「<mark>教學</mark>」。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ 9+ |

### 預設樣式
```css
mark {
    background-color: yellow;
    color: black;
}
```

### 自訂樣式
```html
<!-- 不同顏色的標記 -->
<mark style="background-color: #ff6b6b;">紅色標記</mark>
<mark style="background-color: #4ecdc4;">青色標記</mark>
<mark style="background-color: #ffe66d;">黃色標記</mark>
```

### 使用注意事項
```html
<!-- ✅ 正確：搜尋高亮 -->
<p>找到「<mark>JavaScript</mark>」的相關內容。</p>

<!-- ✅ 正確：重點標記 -->
<p>請注意<mark>截止日期是明天</mark>。</p>

<!-- ❌ 錯誤：用於強調重要性 -->
<p><mark>警告訊息</mark></p>

<!-- ✅ 正確：用 strong -->
<p><strong>警告訊息</strong></p>
```

---

## \<small\> 小字

### 說明
`<small>` 標籤用於次要註釋或小字印刷，如版權聲明、法律文字、免責聲明等。

### 語法
```html
<small>小字內容</small>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 版權聲明
```html
<footer>
    <p>
        <small>&copy; 2026 我的公司. 版權所有.</small>
    </p>
</footer>
```

#### 免責聲明
```html
<p>
    此產品效果因人而異。
    <small>以上僅為示意，實際效果可能有所不同。</small>
</p>
```

#### 細則文字
```html
<p>
    優惠價 NT$ 999
    <small>（原價 NT$ 1,299，限時特惠）</small>
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>這是正常大小的文字。<small>這是較小的文字。</small></p>
<p><small>版權所有 &copy; 2026</small></p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
small {
    font-size: smaller; /* 約 0.83em 或 13.28px */
}
```

### 使用注意事項
```html
<!-- ✅ 正確：法律文字 -->
<p>
    <small>本網站使用 Cookie 以提供更好的服務。</small>
</p>

<!-- ✅ 正確：版權資訊 -->
<footer>
    <small>&copy; 2026 公司名稱</small>
</footer>

<!-- ❌ 錯誤：僅為縮小文字 -->
<small>這是內文</small>

<!-- ✅ 正確：使用 CSS -->
<p style="font-size: 0.8em;">這是內文</p>
```

---

## \<sub\> 下標

### 說明
`<sub>` (subscript) 標籤用於顯示下標文字，常用於化學式、數學式等。

### 語法
```html
文字<sub>下標</sub>
```

### 📌 程式碼範例

#### 化學式
```html
<p>水的化學式是 H<sub>2</sub>O。</p>
<p>二氧化碳是 CO<sub>2</sub>。</p>
```

#### 數學表示
```html
<p>座標點 (x<sub>1</sub>, y<sub>1</sub>)</p>
```

#### 註腳編號
```html
<p>
    這是一段引文<sub>1</sub>。
</p>
<p>
    <sub>1</sub> 引用來源：某書第123頁
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>H<sub>2</sub>O 是水的化學式。</p>
<p>x<sub>1</sub> + x<sub>2</sub> = 10</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
sub {
    vertical-align: sub;
    font-size: smaller;
}
```

### 使用注意事項
```html
<!-- ✅ 正確：化學式 -->
<p>葡萄糖：C<sub>6</sub>H<sub>12</sub>O<sub>6</sub></p>

<!-- ✅ 正確：數學 -->
<p>a<sub>n</sub> = a<sub>1</sub> + (n-1)d</p>

<!-- ❌ 錯誤：純裝飾用途 -->
<p>價格<sub>特惠中</sub></p>

<!-- ✅ 正確：使用 CSS -->
<p>價格<span style="font-size: 0.8em; vertical-align: sub;">特惠中</span></p>
```

---

## \<sup\> 上標

### 說明
`<sup>` (superscript) 標籤用於顯示上標文字，常用於指數、序數、註腳等。

### 語法
```html
文字<sup>上標</sup>
```

### 📌 程式碼範例

#### 數學指數
```html
<p>2<sup>10</sup> = 1024</p>
<p>面積公式：A = πr<sup>2</sup></p>
```

#### 序數
```html
<p>21<sup>st</sup> century</p>
<p>1<sup>st</sup>, 2<sup>nd</sup>, 3<sup>rd</sup></p>
```

#### 註腳參考
```html
<p>
    根據研究顯示<sup>[1]</sup>，這個方法很有效。
</p>
<p>
    <sup>[1]</sup> Smith, J. (2025). "Research Paper"
</p>
```

#### 商標符號
```html
<p>Product<sup>TM</sup></p>
<p>Company<sup>&reg;</sup></p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>E = mc<sup>2</sup></p>
<p>x<sup>2</sup> + y<sup>2</sup> = r<sup>2</sup></p>
<p>21<sup>st</sup> century</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
sup {
    vertical-align: super;
    font-size: smaller;
}
```

### 使用注意事項
```html
<!-- ✅ 正確：數學 -->
<p>10<sup>3</sup> = 1000</p>

<!-- ✅ 正確：註腳 -->
<p>這是引用<sup>1</sup></p>

<!-- ❌ 錯誤：純裝飾 -->
<p>特價<sup>!!</sup></p>

<!-- ✅ 正確：使用適當標籤 -->
<p>特價<strong>!!</strong></p>
```

---

## \<code\> 程式碼

### 說明
`<code>` 標籤用於標記程式碼片段，瀏覽器通常以等寬字型 (monospace) 顯示。

### 語法
```html
<code>程式碼</code>
```

### 📌 程式碼範例

#### 行內程式碼
```html
<p>
    使用 <code>console.log()</code> 可以輸出訊息到控制台。
</p>
```

#### HTML 標籤示例
```html
<p>
    <code>&lt;div&gt;</code> 是一個區塊元素。
</p>
```

#### 與 pre 搭配（多行程式碼）
```html
<pre><code>function hello() {
    console.log('Hello, World!');
}
</code></pre>
```

#### 語法高亮（配合 CSS 類別）
```html
<code class="language-javascript">
const greeting = 'Hello';
</code>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>請輸入 <code>npm install</code> 來安裝套件。</p>
<p>HTML 的段落標籤是 <code>&lt;p&gt;</code>。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
code {
    font-family: monospace;
}
```

### 實際應用：程式碼區塊
```html
<article>
    <h3>JavaScript 範例</h3>
    <p>
        以下是一個簡單的函式，使用
        <code>return</code> 語句回傳值：
    </p>

    <pre><code>function add(a, b) {
    return a + b;
}

// 呼叫函式
const result = add(5, 3);
console.log(result); // 輸出：8
</code></pre>

    <p>
        注意 <code>const</code> 宣告的變數不能重新賦值。
    </p>
</article>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：用於非程式碼 -->
<code>這是普通文字</code>

<!-- ✅ 正確：標記程式碼 -->
<code>console.log()</code>

<!-- ❌ 錯誤：多行程式碼只用 code -->
<code>
function test() {
    return true;
}
</code>

<!-- ✅ 正確：配合 pre 使用 -->
<pre><code>function test() {
    return true;
}
</code></pre>
```

---

## \<pre\> 預格式化文字

### 說明
`<pre>` (preformatted text) 標籤保留文字的空白、換行和縮排，以等寬字型顯示，常用於顯示程式碼或 ASCII 藝術。

### 語法
```html
<pre>
保留格式的文字
    包含空白和縮排
</pre>
```

### 重要特性
- 保留所有空白字元（空格、Tab、換行）
- 使用等寬字型
- 不會自動換行（可能導致水平捲軸）

### 📌 程式碼範例

#### 程式碼區塊
```html
<pre>
function greet(name) {
    console.log('Hello, ' + name);
}

greet('World');
</pre>
```

#### 配合 code 標籤（推薦）
```html
<pre><code class="language-python">
def hello():
    print("Hello, World!")

if __name__ == "__main__":
    hello()
</code></pre>
```

#### ASCII 藝術
```html
<pre>
   /\_/\
  ( o.o )
   > ^ <
</pre>
```

#### 格式化文字
```html
<pre>
姓名        年齡    城市
----------- ------- -----------
張小明      25      台北
李小華      30      台中
王小英      28      高雄
</pre>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<pre>
這是預格式化文字
    保留縮排
        和空白
換行也會保留
</pre>

<pre><code>function example() {
    return "Hello";
}
</code></pre>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
pre {
    display: block;
    font-family: monospace;
    white-space: pre;
    margin: 1em 0;
}
```

### CSS 改進
```html
<!-- 自動換行 -->
<pre style="white-space: pre-wrap;">
很長的程式碼會自動換行，不會產生水平捲軸
</pre>

<!-- 限制寬度和捲軸 -->
<pre style="max-width: 600px; overflow-x: auto; background: #f5f5f5; padding: 10px; border-radius: 5px;">
程式碼內容...
</pre>
```

### 實際應用：程式碼區塊
```html
<article>
    <h3>HTML 基本結構</h3>

    <pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="zh-TW"&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;title&gt;標題&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;h1&gt;Hello World&lt;/h1&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
</article>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：用於一般段落 -->
<pre>
這只是普通的段落文字
</pre>

<!-- ✅ 正確：用 p 標籤 -->
<p>這只是普通的段落文字</p>

<!-- ❌ 錯誤：沒有配合 code -->
<pre>
function test() {}
</pre>

<!-- ✅ 正確：配合 code 使用 -->
<pre><code>
function test() {}
</code></pre>
```

---

## \<kbd\> 鍵盤輸入

### 說明
`<kbd>` (keyboard input) 標籤表示使用者透過鍵盤或其他輸入裝置輸入的內容。

### 語法
```html
<kbd>按鍵</kbd>
```

### 📌 程式碼範例

#### 單一按鍵
```html
<p>按下 <kbd>Enter</kbd> 鍵繼續。</p>
<p>使用 <kbd>Esc</kbd> 關閉視窗。</p>
```

#### 組合鍵
```html
<p>儲存檔案：<kbd>Ctrl</kbd> + <kbd>S</kbd></p>
<p>複製文字：<kbd>Ctrl</kbd> + <kbd>C</kbd></p>
<p>貼上文字：<kbd>Ctrl</kbd> + <kbd>V</kbd></p>
```

#### 巢狀鍵盤輸入
```html
<p>
    同時按下
    <kbd><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd></kbd>
</p>
```

#### 命令列輸入
```html
<p>在終端機輸入：</p>
<p><kbd>npm install express</kbd></p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>按下 <kbd>Enter</kbd> 鍵繼續。</p>
<p>快捷鍵：<kbd>Ctrl</kbd> + <kbd>S</kbd> 儲存檔案。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
kbd {
    font-family: monospace;
}
```

### CSS 美化
```html
<style>
    kbd {
        background-color: #f7f7f7;
        border: 1px solid #ccc;
        border-radius: 3px;
        box-shadow: 0 1px 0 rgba(0,0,0,0.2);
        padding: 2px 6px;
        font-family: monospace;
        font-size: 0.9em;
    }
</style>

<p>按下 <kbd>Ctrl</kbd> + <kbd>C</kbd> 複製。</p>
```

### 使用注意事項
```html
<!-- ✅ 正確：鍵盤按鍵 -->
<p>按 <kbd>F5</kbd> 重新整理頁面。</p>

<!-- ✅ 正確：使用者輸入 -->
<p>輸入 <kbd>help</kbd> 查看說明。</p>

<!-- ❌ 錯誤：用於程式碼輸出 -->
<p>系統回應：<kbd>Command not found</kbd></p>

<!-- ✅ 正確：用 samp -->
<p>系統回應：<samp>Command not found</samp></p>
```

---

## \<samp\> 範例輸出

### 說明
`<samp>` (sample output) 標籤表示程式或系統的輸出範例，通常是電腦產生的文字。

### 語法
```html
<samp>輸出內容</samp>
```

### 📌 程式碼範例

#### 程式輸出
```html
<p>執行後會顯示：<samp>Hello, World!</samp></p>
```

#### 錯誤訊息
```html
<p>如果檔案不存在，會看到：</p>
<p><samp>Error: File not found</samp></p>
```

#### 命令列輸出
```html
<p>輸入 <kbd>node -v</kbd></p>
<p>輸出：<samp>v18.17.0</samp></p>
```

#### 完整範例
```html
<article>
    <h4>執行範例</h4>
    <p>輸入：</p>
    <pre><kbd>python hello.py</kbd></pre>

    <p>輸出：</p>
    <pre><samp>Hello, World!
Program finished.
</samp></pre>
</article>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>系統訊息：<samp>Operation completed successfully</samp></p>
<p>錯誤：<samp>404 Not Found</samp></p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
samp {
    font-family: monospace;
}
```

### 標籤對比

| 標籤 | 用途 | 範例 |
|------|------|------|
| `<kbd>` | 使用者輸入 | `<kbd>Enter</kbd>` |
| `<samp>` | 系統輸出 | `<samp>Done!</samp>` |
| `<code>` | 程式碼 | `<code>console.log()</code>` |
| `<var>` | 變數 | `<var>x</var>` |

### 使用注意事項
```html
<!-- ✅ 正確：系統輸出 -->
<p>結果：<samp>Success</samp></p>

<!-- ✅ 正確：錯誤訊息 -->
<p><samp>Error 500: Internal Server Error</samp></p>

<!-- ❌ 錯誤：用於程式碼 -->
<samp>function test() {}</samp>

<!-- ✅ 正確：用 code -->
<code>function test() {}</code>
```

---

## \<var\> 變數

### 說明
`<var>` (variable) 標籤表示數學表達式或程式中的變數名稱。

### 語法
```html
<var>變數名稱</var>
```

### 📌 程式碼範例

#### 數學表達式
```html
<p>圓的面積公式：A = π<var>r</var><sup>2</sup></p>
<p>如果 <var>x</var> = 5，則 <var>y</var> = 2<var>x</var> + 3 = 13</p>
```

#### 程式變數
```html
<p>
    將值儲存在變數 <var>result</var> 中。
</p>
```

#### 完整範例
```html
<article>
    <h4>二次方程式</h4>
    <p>
        對於方程式
        <var>a</var><var>x</var><sup>2</sup> +
        <var>b</var><var>x</var> +
        <var>c</var> = 0
    </p>
    <p>
        其中 <var>a</var> ≠ 0
    </p>
</article>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>設 <var>x</var> = 10</p>
<p>則 <var>y</var> = <var>x</var> + 5 = 15</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
var {
    font-style: italic;
}
```

### 使用注意事項
```html
<!-- ✅ 正確：數學變數 -->
<p><var>x</var> + <var>y</var> = 10</p>

<!-- ✅ 正確：程式變數名稱 -->
<p>宣告變數 <var>count</var></p>

<!-- ❌ 錯誤：用於程式碼 -->
<var>let count = 0;</var>

<!-- ✅ 正確：用 code -->
<code>let count = 0;</code>
```

---

## \<abbr\> 縮寫

### 說明
`<abbr>` (abbreviation) 標籤用於標記縮寫或首字母縮略詞，通常配合 `title` 屬性顯示完整說明。

### 語法
```html
<abbr title="完整說明">縮寫</abbr>
```

### 常用屬性
| 屬性 | 說明 | 必需 |
|------|------|------|
| `title` | 縮寫的完整說明 | ✅ 強烈建議 |

### 📌 程式碼範例

#### 基本使用
```html
<p>
    <abbr title="HyperText Markup Language">HTML</abbr>
    是網頁的標記語言。
</p>
```

#### 技術縮寫
```html
<p>
    使用
    <abbr title="Cascading Style Sheets">CSS</abbr>
    可以美化網頁。
</p>

<p>
    <abbr title="Application Programming Interface">API</abbr>
    提供程式間的互動介面。
</p>
```

#### 組織名稱
```html
<p>
    <abbr title="World Wide Web Consortium">W3C</abbr>
    是網頁標準組織。
</p>
```

#### 度量單位
```html
<p>
    距離約 10
    <abbr title="公里">km</abbr>。
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>
    <abbr title="HyperText Markup Language">HTML</abbr> 是超文本標記語言。
    （將滑鼠移到 HTML 上會顯示完整說明）
</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
abbr[title] {
    text-decoration: underline dotted;
    cursor: help;
}
```

### 無障礙建議
- ✅ 務必加上 `title` 屬性
- ✅ 第一次出現時可以寫出完整名稱
- ✅ 考慮行動裝置使用者（無法 hover）

### 實際應用
```html
<article>
    <h3>關於網頁技術</h3>
    <p>
        <abbr title="HyperText Markup Language">HTML</abbr>、
        <abbr title="Cascading Style Sheets">CSS</abbr> 和
        <abbr title="JavaScript">JS</abbr>
        是前端開發的三大核心技術。HTML 負責結構，
        CSS 處理樣式，而 JS 提供互動功能。
    </p>

    <p>
        <abbr title="World Wide Web Consortium">W3C</abbr>
        制定了這些技術的標準規範，確保
        <abbr title="搜尋引擎優化">SEO</abbr>
        和無障礙性。
    </p>
</article>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：沒有 title -->
<abbr>HTML</abbr>

<!-- ✅ 正確：包含 title -->
<abbr title="HyperText Markup Language">HTML</abbr>

<!-- ❌ 不需要用 abbr -->
<p>我的 <abbr>名字</abbr> 是...</p>

<!-- ✅ 正確：用於真正的縮寫 -->
<p><abbr title="Doctor">Dr.</abbr> Smith</p>
```

---

## \<cite\> 引用來源

### 說明
`<cite>` 標籤用於標記作品的標題，如書籍、文章、電影、音樂、繪畫等創作作品的名稱。

### 語法
```html
<cite>作品名稱</cite>
```

### 適用範圍
- 書籍、文章標題
- 電影、電視節目
- 音樂專輯、歌曲
- 繪畫、雕塑
- 電腦程式、網站

### 📌 程式碼範例

#### 書籍引用
```html
<p>
    我最近在讀
    <cite>紅樓夢</cite>
    這本經典小說。
</p>
```

#### 文章引用
```html
<p>
    根據
    <cite>HTML 完整指南</cite>
    一文所述...
</p>
```

#### 電影引用
```html
<p>
    <cite>星際效應</cite>
    是一部科幻電影傑作。
</p>
```

#### 配合 blockquote 使用
```html
<blockquote>
    <p>生存還是毀滅，這是一個值得考慮的問題。</p>
    <footer>
        — 莎士比亞，<cite>哈姆雷特</cite>
    </footer>
</blockquote>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>我推薦大家閱讀 <cite>哈利波特</cite> 系列。</p>
<p><cite>全面啟動</cite> 是我最喜歡的電影之一。</p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
cite {
    font-style: italic;
}
```

### 實際應用
```html
<article>
    <h3>推薦書單</h3>

    <ul>
        <li>
            <cite>人類大歷史</cite>
            作者：哈拉瑞
        </li>
        <li>
            <cite>思考，快與慢</cite>
            作者：康納曼
        </li>
        <li>
            <cite>原子習慣</cite>
            作者：詹姆斯·克利爾
        </li>
    </ul>

    <blockquote>
        <p>
            今日事今日畢，明日又有明日事。
        </p>
        <footer>
            出自：<cite>增廣賢文</cite>
        </footer>
    </blockquote>
</article>
```

### 使用注意事項
```html
<!-- ✅ 正確：作品標題 -->
<p>電影 <cite>教父</cite> 是經典之作。</p>

<!-- ❌ 錯誤：人名不用 cite -->
<p><cite>莎士比亞</cite> 是偉大的劇作家。</p>

<!-- ✅ 正確：人名不需特殊標記 -->
<p>莎士比亞是偉大的劇作家。</p>

<!-- ✅ 正確：作品名用 cite -->
<p>莎士比亞的 <cite>羅密歐與茱麗葉</cite> 是愛情悲劇。</p>
```

---

## \<q\> 行內引用

### 說明
`<q>` (quotation) 標籤用於標記短的行內引用文字，瀏覽器通常會自動加上引號。

### 語法
```html
<q>引用內容</q>
```

### 常用屬性
| 屬性 | 說明 | 值 |
|------|------|-----|
| `cite` | 引用來源的 URL | URL 連結 |

### 📌 程式碼範例

#### 基本使用
```html
<p>
    愛因斯坦說過：
    <q>想像力比知識更重要。</q>
</p>
```

#### 加上來源 URL
```html
<p>
    根據報導
    <q cite="https://example.com/article">
        全球氣溫持續上升
    </q>。
</p>
```

#### 巢狀引用
```html
<p>
    他說：
    <q>她告訴我
        <q>明天會是晴天</q>
    </q>。
</p>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<p>孔子說：<q>學而不思則罔，思而不學則殆。</q></p>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
瀏覽器會自動加上引號（中文通常是「」，英文是 ""）

### \<q\> vs 手動引號

| 方式 | 優點 | 缺點 |
|------|------|------|
| `<q>` | 語意化，引號自動適應語言 | 樣式較難控制 |
| `"手動"` | 完全控制樣式 | 無語意，不同語言需手動調整 |

### 使用注意事項
```html
<!-- ✅ 正確：短引用用 q -->
<p>他說：<q>我同意</q>。</p>

<!-- ❌ 錯誤：長引用用 q -->
<q>
    這是一段很長的引用文字，
    包含多個句子和段落...
</q>

<!-- ✅ 正確：長引用用 blockquote -->
<blockquote>
    <p>這是一段很長的引用文字，</p>
    <p>包含多個句子和段落...</p>
</blockquote>
```

---

## \<blockquote\> 區塊引用

### 說明
`<blockquote>` 標籤用於標記長篇幅的引用內容，通常是一個或多個段落。瀏覽器會自動縮排顯示。

### 語法
```html
<blockquote cite="來源URL">
    <p>引用內容</p>
</blockquote>
```

### 常用屬性
| 屬性 | 說明 | 值 |
|------|------|-----|
| `cite` | 引用來源的 URL | URL 連結 |

### 📌 程式碼範例

#### 基本使用
```html
<blockquote>
    <p>
        生存還是毀滅，這是一個值得考慮的問題：
        默然忍受命運的暴虐的毒箭，
        或是挺身反抗人世的無涯的苦難，
        通過鬥爭把它們掃清，這兩種行為，哪一種更高貴？
    </p>
</blockquote>
```

#### 加上來源
```html
<blockquote cite="https://example.com/article">
    <p>
        人工智慧正在改變我們的生活方式，
        從醫療診斷到自動駕駛，AI 的應用無處不在。
    </p>
    <footer>
        — <cite>科技趨勢雜誌</cite>，2026 年 1 月
    </footer>
</blockquote>
```

#### 多段引用
```html
<blockquote>
    <p>第一段引用內容...</p>
    <p>第二段引用內容...</p>
    <p>第三段引用內容...</p>
</blockquote>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<blockquote>
    <p>
        路漫漫其修遠兮，吾將上下而求索。
    </p>
    <footer>— 屈原，<cite>離騷</cite></footer>
</blockquote>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
blockquote {
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 40px;
    margin-inline-end: 40px;
}
```

### 實際應用：完整引用格式
```html
<article>
    <h3>關於學習</h3>

    <blockquote cite="https://example.com/quotes">
        <p>
            我們一生的學習不應該僅限於學校，
            而應該是一個持續終身的過程。
            只有不斷學習，才能跟上時代的步伐。
        </p>
        <footer>
            — 張小明，
            <cite>
                <a href="https://example.com/book">
                    終身學習之道
                </a>
            </cite>
            (2025)
        </footer>
    </blockquote>
</article>
```

### CSS 美化
```html
<style>
    blockquote {
        border-left: 4px solid #ccc;
        padding-left: 20px;
        margin: 20px 0;
        font-style: italic;
        color: #555;
        background-color: #f9f9f9;
    }

    blockquote footer {
        margin-top: 10px;
        font-size: 0.9em;
        text-align: right;
    }
</style>

<blockquote>
    <p>知識就是力量。</p>
    <footer>— 培根</footer>
</blockquote>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：用於縮排 -->
<blockquote>
    <p>這只是想要縮排，不是引用</p>
</blockquote>

<!-- ✅ 正確：用 CSS 縮排 -->
<p style="margin-left: 40px;">這是縮排的段落</p>

<!-- ❌ 錯誤：短引用用 blockquote -->
<blockquote>好的</blockquote>

<!-- ✅ 正確：短引用用 q -->
<p>他說：<q>好的</q>。</p>

<!-- ✅ 正確：長引用用 blockquote -->
<blockquote>
    <p>這是一段較長的引用文字...</p>
</blockquote>
```

---

## 最佳實踐總結

### 語意化選擇指南

| 用途 | 選擇標籤 |
|------|---------|
| 重要性強調 | `<strong>` |
| 語氣強調 | `<em>` |
| 視覺粗體（無語意） | `<b>` 或 CSS |
| 視覺斜體（無語意） | `<i>` 或 CSS |
| 程式碼 | `<code>` + `<pre>` |
| 鍵盤輸入 | `<kbd>` |
| 系統輸出 | `<samp>` |
| 變數名稱 | `<var>` |
| 作品標題 | `<cite>` |
| 短引用 | `<q>` |
| 長引用 | `<blockquote>` |
| 縮寫 | `<abbr>` |

### 常見錯誤
1. ❌ 為了樣式而選擇標籤（應該用 CSS）
2. ❌ 過度使用 `<div>` 和 `<span>`（應優先考慮語意標籤）
3. ❌ 連續使用多個 `<br>` 製造空白（應該用 CSS margin）
4. ❌ 巢狀段落標籤
5. ❌ 使用 `<u>` 模擬連結

### 無障礙提示
- ✅ 優先使用語意標籤，幫助螢幕閱讀器理解內容
- ✅ 確保標題有合理的層級結構
- ✅ 為縮寫加上 `title` 屬性
- ✅ 引用內容要有明確的來源

---

[⬆️ 回到頂部](#文字內容標籤) | [📑 回索引頁](index.md)
