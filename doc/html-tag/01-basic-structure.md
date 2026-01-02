# 基本結構標籤

> HTML 文件的基礎架構標籤

## 📑 目錄

- [<!DOCTYPE>](#doctype)
- [\<html\>](#html)
- [\<head\>](#head)
- [\<body\>](#body)
- [\<title\>](#title)
- [完整文件結構範例](#完整文件結構範例)

---

## <!DOCTYPE>

### 說明
`<!DOCTYPE>` 宣告用於告知瀏覽器該文件使用的 HTML 版本。它必須是 HTML 文件的第一行，且不區分大小寫。

### 語法
```html
<!DOCTYPE html>
```

### 重要特性
- **不是 HTML 標籤**，而是指令 (instruction)
- **HTML5** 使用簡化的宣告 `<!DOCTYPE html>`
- **必須放在文件最前面**，在 `<html>` 之前
- **不需要關閉標籤**

### 歷史版本對照

| HTML 版本 | DOCTYPE 宣告 |
|-----------|-------------|
| HTML5 | `<!DOCTYPE html>` ✅ |
| HTML 4.01 Strict | `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">` |
| XHTML 1.0 | `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">` |

### 📌 程式碼範例
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>我的網頁</title>
</head>
<body>
    <h1>歡迎</h1>
</body>
</html>
```

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ 9+ |

### 使用注意事項
- ⚠️ 缺少 DOCTYPE 會導致瀏覽器進入「怪異模式」(Quirks Mode)，造成排版錯誤
- ✅ 務必使用 HTML5 的簡化版本 `<!DOCTYPE html>`
- ✅ 確保 DOCTYPE 前沒有任何空白或註解

---

## \<html\>

### 說明
`<html>` 是 HTML 文件的根元素，包含整個網頁的所有內容。所有其他標籤都必須是它的子元素。

### 語法
```html
<html lang="語言代碼">
  <!-- 文件內容 -->
</html>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `lang` | 指定文件的主要語言 | 語言代碼（如 `zh-TW`, `en`, `ja`） | ✅ 強烈建議 |
| `dir` | 文字方向 | `ltr` (左到右), `rtl` (右到左) | ❌ |
| `xmlns` | XML 命名空間（僅 XHTML） | `http://www.w3.org/1999/xhtml` | ❌ |

### 語言代碼參考

| 語言 | 代碼 |
|------|------|
| 繁體中文（台灣） | `zh-TW` |
| 簡體中文（中國） | `zh-CN` |
| 英文（美國） | `en-US` |
| 英文（英國） | `en-GB` |
| 日文 | `ja` |
| 韓文 | `ko` |
| 法文 | `fr` |
| 德文 | `de` |
| 西班牙文 | `es` |

### 📌 程式碼範例
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>繁體中文網頁</title>
</head>
<body>
    <h1>你好，世界！</h1>
</body>
</html>
```

### 雙語網頁範例
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>雙語網站</title>
</head>
<body>
    <div lang="zh-TW">
        <h1>繁體中文標題</h1>
        <p>這是中文內容</p>
    </div>

    <div lang="en">
        <h1>English Title</h1>
        <p>This is English content</p>
    </div>
</body>
</html>
```

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議
- ✅ **必須設定 `lang` 屬性**，幫助螢幕閱讀器正確發音
- ✅ 語言代碼要準確（如台灣繁體用 `zh-TW` 而非 `zh`）
- ✅ 如果頁面有多語言區塊，在對應元素上設定 `lang` 屬性

### 使用注意事項
- ⚠️ 每個 HTML 文件只能有一個 `<html>` 標籤
- ⚠️ `<html>` 必須是 `<!DOCTYPE>` 之後的第一個標籤
- ✅ 一定要包含 `lang` 屬性以提升 SEO 和無障礙性

---

## \<head\>

### 說明
`<head>` 包含文件的元數據（metadata），這些資訊不會直接顯示在網頁上，但對瀏覽器、搜尋引擎和網頁功能至關重要。

### 語法
```html
<head>
  <!-- 元數據內容 -->
</head>
```

### 可包含的標籤

| 標籤 | 用途 | 必需 |
|------|------|------|
| `<title>` | 網頁標題 | ✅ 必需 |
| `<meta>` | 元數據（編碼、描述、關鍵字等） | ✅ 強烈建議 |
| `<link>` | 外部資源連結（CSS、圖示等） | ❌ |
| `<style>` | 內嵌 CSS 樣式 | ❌ |
| `<script>` | JavaScript 程式碼 | ❌ |
| `<base>` | 基準 URL | ❌ |
| `<noscript>` | 不支援 JavaScript 時的替代內容 | ❌ |

### 📌 程式碼範例

#### 基本 head 結構
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>網頁標題</title>
    <meta name="description" content="網頁描述">
    <link rel="stylesheet" href="styles.css">
</head>
```

#### 完整的 head 範例
```html
<head>
    <!-- 編碼宣告 -->
    <meta charset="UTF-8">

    <!-- 行動裝置視窗設定 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- IE 相容性 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">

    <!-- 網頁標題 -->
    <title>我的網站 - 首頁</title>

    <!-- SEO 元數據 -->
    <meta name="description" content="這是一個關於 HTML 教學的網站">
    <meta name="keywords" content="HTML, 教學, 網頁設計">
    <meta name="author" content="作者名稱">

    <!-- Open Graph (社群媒體分享) -->
    <meta property="og:title" content="我的網站">
    <meta property="og:description" content="網站描述">
    <meta property="og:image" content="https://example.com/image.jpg">
    <meta property="og:url" content="https://example.com">

    <!-- 網站圖示 -->
    <link rel="icon" type="image/png" href="favicon.png">

    <!-- CSS 樣式表 -->
    <link rel="stylesheet" href="styles.css">

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC&display=swap" rel="stylesheet">

    <!-- JavaScript -->
    <script src="script.js" defer></script>
</head>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

`<head>` 標籤內的內容不會在網頁上顯示，但會影響：
- 瀏覽器分頁標題
- 搜尋引擎結果
- 社群媒體分享預覽
- 網頁的外觀和功能

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### SEO 最佳實踐
- ✅ 必須包含 `<meta charset="UTF-8">`
- ✅ 必須包含 `<meta name="viewport">` 以支援行動裝置
- ✅ `<title>` 長度建議在 50-60 字元以內
- ✅ `<meta name="description">` 長度建議在 150-160 字元
- ✅ 使用 Open Graph 標籤提升社群媒體分享效果

### 使用注意事項
- ⚠️ `<meta charset>` 必須在前 1024 個位元組內
- ⚠️ 每個文件只能有一個 `<head>` 標籤
- ✅ 將 JavaScript 放在 `</body>` 前或使用 `defer`/`async` 屬性以提升效能

---

## \<body\>

### 說明
`<body>` 包含網頁的所有可見內容，包括文字、圖片、影片、連結等。所有使用者能看到的內容都必須放在 `<body>` 標籤內。

### 語法
```html
<body>
  <!-- 可見內容 -->
</body>
```

### 常用屬性（HTML5 已廢棄，建議用 CSS）

| 屬性 | 說明 | 狀態 |
|------|------|------|
| `bgcolor` | 背景顏色 | ❌ 已廢棄，使用 CSS `background-color` |
| `text` | 文字顏色 | ❌ 已廢棄，使用 CSS `color` |
| `background` | 背景圖片 | ❌ 已廢棄，使用 CSS `background-image` |
| `onload` | 頁面載入事件 | ⚠️ 建議使用 JavaScript |

### 📌 程式碼範例

#### 基本結構
```html
<body>
    <h1>歡迎來到我的網站</h1>
    <p>這是一段文字內容。</p>
    <img src="image.jpg" alt="圖片描述">
    <a href="https://example.com">點擊連結</a>
</body>
```

#### 語意化結構（推薦）
```html
<body>
    <header>
        <h1>網站名稱</h1>
        <nav>
            <ul>
                <li><a href="/">首頁</a></li>
                <li><a href="/about">關於</a></li>
                <li><a href="/contact">聯絡</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <h2>文章標題</h2>
            <p>文章內容...</p>
        </article>
    </main>

    <footer>
        <p>&copy; 2026 版權所有</p>
    </footer>
</body>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

`<body>` 標籤內的所有內容都會顯示在瀏覽器視窗中，包括：

<h1>這是標題</h1>
<p>這是段落文字。</p>
<ul>
    <li>列表項目 1</li>
    <li>列表項目 2</li>
</ul>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議
- ✅ 使用語意化標籤（`<header>`, `<nav>`, `<main>`, `<footer>`）
- ✅ 確保內容有邏輯結構和正確的標題層級
- ✅ 為圖片加上 `alt` 屬性
- ✅ 確保鍵盤可以操作所有互動元素

### 使用注意事項
- ⚠️ 每個 HTML 文件只能有一個 `<body>` 標籤
- ⚠️ 不要使用已廢棄的屬性（如 `bgcolor`），改用 CSS
- ✅ 建議使用 HTML5 語意化標籤組織內容

---

## \<title\>

### 說明
`<title>` 定義網頁的標題，顯示在瀏覽器分頁、書籤和搜尋引擎結果中。這是 SEO 最重要的元素之一。

### 語法
```html
<title>網頁標題</title>
```

### 重要特性
- **必須放在 `<head>` 內**
- **每個文件只能有一個 `<title>`**
- **僅接受純文字**，不支援 HTML 標籤
- **會顯示在瀏覽器分頁**
- **影響搜尋引擎排名**

### 📌 程式碼範例

#### 首頁標題
```html
<head>
    <title>我的網站 - 專業網頁設計服務</title>
</head>
```

#### 內頁標題
```html
<head>
    <title>關於我們 | 我的網站</title>
</head>
```

#### 文章頁標題
```html
<head>
    <title>HTML 教學：基本結構標籤完整指南 - 我的網站</title>
</head>
```

#### 動態標題（JavaScript）
```html
<head>
    <title id="pageTitle">載入中...</title>
    <script>
        document.getElementById('pageTitle').textContent = '動態更新的標題';
    </script>
</head>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

`<title>` 標籤的內容會顯示在：
1. **瀏覽器分頁**：顯示在瀏覽器視窗頂端
2. **書籤**：儲存網頁時的預設名稱
3. **搜尋結果**：Google 等搜尋引擎的標題連結
4. **社群分享**：分享到社群媒體時的標題

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### SEO 最佳實踐

#### 標題長度
- ✅ **建議長度**：50-60 字元（中文約 25-30 字）
- ⚠️ 超過 60 字元會在搜尋結果中被截斷

#### 標題格式

| 頁面類型 | 建議格式 | 範例 |
|---------|---------|------|
| 首頁 | 品牌名 - 主要關鍵字 | `ABC 公司 - 專業網頁設計服務` |
| 分類頁 | 分類名 \| 品牌名 | `產品列表 \| ABC 公司` |
| 內容頁 | 內容標題 - 品牌名 | `如何學習 HTML - ABC 公司` |

#### 標題撰寫技巧
```html
<!-- ❌ 不佳範例 -->
<title>首頁</title>
<title>歡迎</title>
<title>AAAAAA - 最好的網站！！！</title>

<!-- ✅ 良好範例 -->
<title>ABC 科技 - 提供創新的軟體解決方案</title>
<title>HTML 完整教學指南 - 從入門到精通 | 網頁學習網</title>
```

### 無障礙建議
- ✅ 標題要清楚描述頁面內容
- ✅ 不同頁面要有不同的標題
- ✅ 避免使用特殊符號和全大寫
- ✅ 標題要有意義，不要只寫「頁面」或「網站」

### 使用注意事項
- ⚠️ 不要在 `<title>` 內使用 HTML 標籤（會被視為純文字）
- ⚠️ 避免關鍵字堆疊（keyword stuffing）
- ✅ 每個頁面都要有獨特的標題
- ✅ 將最重要的關鍵字放在前面
- ✅ 包含品牌名稱以建立識別度

---

## 完整文件結構範例

### 標準 HTML5 文件
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <!-- 必要的元數據 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">

    <!-- 標題和描述 -->
    <title>我的網站 - 首頁</title>
    <meta name="description" content="這是一個完整的 HTML5 網頁範例">
    <meta name="keywords" content="HTML5, 網頁設計, 教學">
    <meta name="author" content="作者名稱">

    <!-- 網站圖示 -->
    <link rel="icon" type="image/png" href="favicon.png">

    <!-- CSS -->
    <link rel="stylesheet" href="styles.css">

    <!-- JavaScript -->
    <script src="script.js" defer></script>
</head>
<body>
    <!-- 頁首 -->
    <header>
        <h1>網站標題</h1>
        <nav>
            <ul>
                <li><a href="/">首頁</a></li>
                <li><a href="/about">關於</a></li>
                <li><a href="/contact">聯絡</a></li>
            </ul>
        </nav>
    </header>

    <!-- 主要內容 -->
    <main>
        <article>
            <h2>歡迎來到我的網站</h2>
            <p>這是主要內容區域。</p>
        </article>
    </main>

    <!-- 側邊欄 -->
    <aside>
        <h3>相關連結</h3>
        <ul>
            <li><a href="#">連結 1</a></li>
            <li><a href="#">連結 2</a></li>
        </ul>
    </aside>

    <!-- 頁尾 -->
    <footer>
        <p>&copy; 2026 版權所有</p>
    </footer>
</body>
</html>
```

### 實際應用：部落格文章頁面
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>如何學習 HTML - 完整入門指南 | 程式學習部落格</title>
    <meta name="description" content="從零開始學習 HTML，本文提供完整的入門指南，包含實用範例和練習題">
    <meta name="keywords" content="HTML, 教學, 程式設計, 網頁開發">
    <meta name="author" content="張小明">

    <!-- Open Graph -->
    <meta property="og:title" content="如何學習 HTML - 完整入門指南">
    <meta property="og:description" content="從零開始學習 HTML 的完整指南">
    <meta property="og:type" content="article">
    <meta property="og:url" content="https://example.com/learn-html">
    <meta property="og:image" content="https://example.com/images/html-tutorial.jpg">

    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header>
        <div class="logo">
            <h1>程式學習部落格</h1>
        </div>
        <nav>
            <ul>
                <li><a href="/">首頁</a></li>
                <li><a href="/tutorials">教學</a></li>
                <li><a href="/blog">部落格</a></li>
                <li><a href="/about">關於</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <header>
                <h2>如何學習 HTML - 完整入門指南</h2>
                <p class="meta">
                    <time datetime="2026-01-02">2026 年 1 月 2 日</time>
                    <span>作者：張小明</span>
                </p>
            </header>

            <section>
                <h3>什麼是 HTML？</h3>
                <p>HTML (HyperText Markup Language) 是網頁的骨架...</p>
            </section>

            <section>
                <h3>基本結構</h3>
                <p>每個 HTML 文件都包含以下基本結構...</p>
            </section>
        </article>

        <aside>
            <h3>相關文章</h3>
            <ul>
                <li><a href="#">CSS 入門教學</a></li>
                <li><a href="#">JavaScript 基礎</a></li>
            </ul>
        </aside>
    </main>

    <footer>
        <p>&copy; 2026 程式學習部落格. 版權所有.</p>
        <nav>
            <a href="/privacy">隱私政策</a>
            <a href="/terms">使用條款</a>
        </nav>
    </footer>
</body>
</html>
```

---

## 最佳實踐總結

### ✅ 必須做的事
1. 始終包含 `<!DOCTYPE html>`
2. 設定 `<html lang="語言代碼">`
3. 在 `<head>` 中加入 `<meta charset="UTF-8">`
4. 加入 viewport meta 標籤以支援行動裝置
5. 為每個頁面設定獨特的 `<title>`
6. 使用語意化標籤組織 `<body>` 內容

### ❌ 避免的事
1. 不要省略 DOCTYPE
2. 不要在 body 使用已廢棄的屬性（bgcolor, text 等）
3. 不要讓 title 過長或堆疊關鍵字
4. 不要在 head 放置可見內容

### 🎯 進階優化
1. 使用 Open Graph 標籤提升社群分享效果
2. 加入結構化資料（Schema.org）提升 SEO
3. 優化頁面載入速度（CSS 在 head，JS 在 body 底部或使用 defer）
4. 確保無障礙性（ARIA 標籤、語意化結構）

---

[⬆️ 回到頂部](#基本結構標籤) | [📑 回索引頁](index.md)
