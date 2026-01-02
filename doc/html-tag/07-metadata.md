# 元數據標籤 (Metadata Elements)

> 元數據標籤定義關於 HTML 文件的資訊，這些資訊不會直接顯示在網頁上，但對搜尋引擎、瀏覽器和其他網路服務非常重要。

## 📑 目錄

- [`<meta>` - 元數據](#meta---元數據)
  - [charset - 字元編碼](#charset---字元編碼)
  - [viewport - 視口設定](#viewport---視口設定)
  - [description - 網頁描述](#description---網頁描述)
  - [keywords - 關鍵字](#keywords---關鍵字)
  - [author - 作者](#author---作者)
  - [robots - 搜尋引擎指令](#robots---搜尋引擎指令)
  - [http-equiv - HTTP 標頭](#http-equiv---http-標頭)
  - [Open Graph - 社群媒體](#open-graph---社群媒體)
  - [Twitter Card - Twitter 卡片](#twitter-card---twitter-卡片)
  - [theme-color - 主題顏色](#theme-color---主題顏色)
- [`<link>` - 外部資源連結](#link---外部資源連結)
  - [stylesheet - 樣式表](#stylesheet---樣式表)
  - [icon - 網站圖示](#icon---網站圖示)
  - [preload/prefetch - 預載資源](#preloadprefetch---預載資源)
  - [canonical - 標準網址](#canonical---標準網址)
  - [alternate - 替代版本](#alternate---替代版本)
- [`<style>` - 內嵌樣式](#style---內嵌樣式)
- [`<script>` - JavaScript](#script---javascript)
  - [defer - 延遲執行](#defer---延遲執行)
  - [async - 非同步載入](#async---非同步載入)
  - [module - ES 模組](#module---es-模組)
- [`<base>` - 基準 URL](#base---基準-url)
- [`<noscript>` - JavaScript 替代內容](#noscript---javascript-替代內容)
- [完整 Head 範例](#完整-head-範例)
- [SEO 優化指南](#seo-優化指南)
- [效能優化指南](#效能優化指南)
- [最佳實踐總結](#最佳實踐總結)

---

## `<meta>` - 元數據

### 說明
`<meta>` 標籤提供關於 HTML 文件的元數據（metadata），這些資訊用於搜尋引擎、瀏覽器和其他網路服務。

### 語法
```html
<meta name="名稱" content="內容">
<meta charset="字元編碼">
<meta http-equiv="標頭名稱" content="值">
<meta property="屬性" content="內容">
```

### 常用屬性

| 屬性 | 說明 | 用途 |
|------|------|------|
| `name` | 元數據名稱 | 定義元數據類型 |
| `content` | 元數據內容 | 提供實際的值 |
| `charset` | 字元編碼 | 定義文件編碼 |
| `http-equiv` | HTTP 標頭 | 模擬 HTTP 回應標頭 |
| `property` | 屬性（用於 Open Graph） | 社群媒體元數據 |

---

### charset - 字元編碼

#### 說明
定義 HTML 文件的字元編碼，應該是 `<head>` 中的第一個元素。

#### 📌 程式碼範例

```html
<!-- 必須：UTF-8 編碼 -->
<meta charset="UTF-8">

<!-- 完整 head 開頭 -->
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <title>網頁標題</title>
</head>
```

#### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

#### 使用注意事項

```html
<!-- ✅ 正確：放在 head 最前面 -->
<head>
  <meta charset="UTF-8">
  <title>...</title>
</head>

<!-- ❌ 錯誤：放在後面 -->
<head>
  <title>...</title>
  <meta charset="UTF-8"> <!-- 太晚了 -->
</head>

<!-- ✅ 正確：使用 UTF-8 -->
<meta charset="UTF-8">

<!-- ❌ 過時：舊的寫法 -->
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
```

---

### viewport - 視口設定

#### 說明
控制頁面在行動裝置上的顯示方式，對響應式網頁設計至關重要。

#### 📌 程式碼範例

```html
<!-- 標準 viewport 設定 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- 不允許縮放 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">

<!-- 限制縮放範圍 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=3.0">

<!-- 固定寬度 -->
<meta name="viewport" content="width=375">
```

#### viewport 參數說明

| 參數 | 說明 | 常用值 |
|------|------|--------|
| `width` | 視口寬度 | `device-width` 或數字（px） |
| `height` | 視口高度 | `device-height` 或數字（px） |
| `initial-scale` | 初始縮放比例 | `1.0`（100%） |
| `minimum-scale` | 最小縮放比例 | `0.5` - `1.0` |
| `maximum-scale` | 最大縮放比例 | `1.0` - `5.0` |
| `user-scalable` | 使用者可否縮放 | `yes` 或 `no` |

#### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ 10+ |

#### 使用注意事項

```html
<!-- ✅ 正確：標準設定 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- ⚠️ 不建議：禁止縮放（影響無障礙性） -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">

<!-- ❌ 錯誤：沒有 viewport（行動裝置體驗差） -->
<!-- 完全沒有 viewport meta 標籤 -->
```

---

### description - 網頁描述

#### 說明
提供網頁內容的簡短描述，顯示在搜尋引擎結果中。

#### 📌 程式碼範例

```html
<!-- 基本描述 -->
<meta name="description" content="HTML5 完整教學，涵蓋所有標籤的詳細說明、範例和最佳實踐。">

<!-- 部落格文章 -->
<meta name="description" content="學習如何使用 HTML5 語意化標籤建立更好的網頁結構，提升 SEO 和無障礙性。">

<!-- 產品頁面 -->
<meta name="description" content="iPhone 15 Pro，搭載 A17 Pro 晶片，48MP 相機，6.1 吋螢幕。優惠價 NT$36,900。">

<!-- 首頁 -->
<meta name="description" content="ABC 科技公司提供專業的網頁開發、UI/UX 設計和數位行銷服務。立即聯絡我們！">
```

#### 最佳實踐

- **長度**: 150-160 個字元（中文約 70-80 字）
- **內容**: 準確描述頁面內容
- **關鍵字**: 自然包含重要關鍵字
- **獨特性**: 每個頁面都應該有不同的描述
- **行動呼籲**: 可以包含 CTA（如「立即了解」）

#### 使用注意事項

```html
<!-- ✅ 正確：簡潔、準確、有吸引力 -->
<meta name="description" content="學習 HTML5 的完整指南，包含所有標籤說明、實用範例和最佳實踐。適合初學者到進階開發者。">

<!-- ❌ 錯誤：太短 -->
<meta name="description" content="HTML 教學">

<!-- ❌ 錯誤：太長（會被截斷） -->
<meta name="description" content="這是一個非常詳細的 HTML5 教學網站，我們提供了所有你需要知道的關於 HTML5 的資訊，包括但不限於各種標籤的使用方法、屬性說明、瀏覽器支援情況、實際應用範例、最佳實踐建議、SEO 優化技巧、無障礙設計原則等等內容...">

<!-- ❌ 錯誤：關鍵字堆砌 -->
<meta name="description" content="HTML, HTML5, 網頁, 網頁設計, 網頁開發, 前端, 教學, 標籤">
```

---

### keywords - 關鍵字

#### 說明
定義網頁的關鍵字。**注意**: 現代搜尋引擎（如 Google）已經不使用此標籤。

#### 📌 程式碼範例

```html
<!-- 基本用法（但效果有限） -->
<meta name="keywords" content="HTML5, 網頁開發, 前端, 教學, 標籤">

<!-- 多個關鍵字 -->
<meta name="keywords" content="JavaScript, React, Vue, Angular, 前端框架">
```

#### 使用注意事項

```html
<!-- ⚠️ 注意：Google 不使用此標籤 -->
<meta name="keywords" content="...">

<!-- ✅ 更重要：專注於 description 和內容品質 -->
<meta name="description" content="高品質的描述">
<h1>使用適當的標題</h1>
<p>提供有價值的內容...</p>
```

---

### author - 作者

#### 說明
定義網頁的作者。

#### 📌 程式碼範例

```html
<!-- 作者姓名 -->
<meta name="author" content="張三">

<!-- 作者和 Email -->
<meta name="author" content="張三 (zhang@example.com)">

<!-- 公司名稱 -->
<meta name="author" content="ABC 科技有限公司">
```

---

### robots - 搜尋引擎指令

#### 說明
告訴搜尋引擎爬蟲如何處理此頁面。

#### 📌 程式碼範例

```html
<!-- 允許索引和跟隨連結（預設） -->
<meta name="robots" content="index, follow">

<!-- 不索引此頁面 -->
<meta name="robots" content="noindex, follow">

<!-- 不跟隨此頁面的連結 -->
<meta name="robots" content="index, nofollow">

<!-- 完全不處理 -->
<meta name="robots" content="noindex, nofollow">

<!-- 不顯示快取連結 -->
<meta name="robots" content="index, follow, noarchive">

<!-- 不顯示摘要 -->
<meta name="robots" content="index, follow, nosnippet">

<!-- 不索引圖片 -->
<meta name="robots" content="index, follow, noimageindex">

<!-- 指定特定搜尋引擎 -->
<meta name="googlebot" content="noindex, nofollow">
<meta name="bingbot" content="index, follow">
```

#### robots 指令說明

| 指令 | 說明 |
|------|------|
| `index` | 允許索引此頁面 |
| `noindex` | 不索引此頁面 |
| `follow` | 跟隨此頁面的連結 |
| `nofollow` | 不跟隨此頁面的連結 |
| `noarchive` | 不顯示「庫存頁庫」連結 |
| `nosnippet` | 不在搜尋結果中顯示摘要 |
| `noimageindex` | 不索引此頁面的圖片 |
| `none` | 等同於 `noindex, nofollow` |
| `all` | 等同於 `index, follow`（預設） |

#### 使用場景

```html
<!-- 登入頁面：不需要被索引 -->
<meta name="robots" content="noindex, nofollow">

<!-- 感謝頁面：索引但不跟隨連結 -->
<meta name="robots" content="index, nofollow">

<!-- 測試頁面：完全不處理 -->
<meta name="robots" content="noindex, nofollow">

<!-- 一般公開頁面：允許索引（可省略，因為是預設值） -->
<meta name="robots" content="index, follow">
<!-- 或完全省略 -->
```

---

### http-equiv - HTTP 標頭

#### 說明
模擬 HTTP 回應標頭的行為。

#### 📌 程式碼範例

```html
<!-- 內容類型和字元編碼（舊式，不建議） -->
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<!-- 改用 -->
<meta charset="UTF-8">

<!-- 重新整理和重新導向 -->
<meta http-equiv="refresh" content="30">
<meta http-equiv="refresh" content="5; url=https://example.com">

<!-- 相容性模式（IE） -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">

<!-- 內容安全政策 -->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'">

<!-- 快取控制 -->
<meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate">
<meta http-equiv="Pragma" content="no-cache">
<meta http-equiv="Expires" content="0">
```

#### 使用注意事項

```html
<!-- ⚠️ 不建議：用 meta 重新導向 -->
<meta http-equiv="refresh" content="0; url=https://new-site.com">
<!-- 建議：使用伺服器端 301 重新導向 -->

<!-- ✅ 可接受：倒數計時重新導向 -->
<meta http-equiv="refresh" content="5; url=https://example.com">
<p>5 秒後將自動跳轉...</p>

<!-- ⚠️ 過時：IE 相容性（現代開發較少需要） -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

---

### Open Graph - 社群媒體

#### 說明
Open Graph 協定讓網頁在社群媒體（Facebook、LinkedIn 等）上分享時有更好的呈現。

#### 📌 程式碼範例

```html
<!-- 基本 Open Graph 標籤 -->
<meta property="og:title" content="網頁標題">
<meta property="og:description" content="網頁描述">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com/page">
<meta property="og:type" content="website">

<!-- 完整範例：部落格文章 -->
<meta property="og:title" content="HTML5 語意化標籤完整指南">
<meta property="og:description" content="深入了解 HTML5 所有語意化標籤的使用方法和最佳實踐">
<meta property="og:image" content="https://example.com/images/html5-guide.jpg">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:url" content="https://example.com/blog/html5-semantic-tags">
<meta property="og:type" content="article">
<meta property="og:site_name" content="我的技術部落格">
<meta property="og:locale" content="zh_TW">

<!-- 文章特定標籤 -->
<meta property="article:published_time" content="2026-01-02T14:30:00+08:00">
<meta property="article:modified_time" content="2026-01-02T16:00:00+08:00">
<meta property="article:author" content="張三">
<meta property="article:section" content="網頁開發">
<meta property="article:tag" content="HTML5">
<meta property="article:tag" content="語意化">

<!-- 產品頁面 -->
<meta property="og:type" content="product">
<meta property="og:title" content="iPhone 15 Pro">
<meta property="og:description" content="最新旗艦手機，搭載 A17 Pro 晶片">
<meta property="og:image" content="https://example.com/iphone15.jpg">
<meta property="og:url" content="https://example.com/products/iphone15pro">
<meta property="product:price:amount" content="36900">
<meta property="product:price:currency" content="TWD">
```

#### 常用 Open Graph 標籤

| 標籤 | 說明 | 必需 |
|------|------|------|
| `og:title` | 標題 | ✅ |
| `og:description` | 描述 | ✅ |
| `og:image` | 圖片 URL | ✅ |
| `og:url` | 頁面 URL | ✅ |
| `og:type` | 類型（website, article, product 等） | ✅ |
| `og:site_name` | 網站名稱 | ⚪ |
| `og:locale` | 語系 | ⚪ |
| `og:image:width` | 圖片寬度 | ⚪ |
| `og:image:height` | 圖片高度 | ⚪ |

#### 圖片尺寸建議

- **Facebook**: 1200 x 630 px（比例 1.91:1）
- **最小尺寸**: 600 x 315 px
- **最大檔案**: 8 MB

---

### Twitter Card - Twitter 卡片

#### 說明
Twitter Card 讓網頁在 Twitter 上分享時有更豐富的呈現。

#### 📌 程式碼範例

```html
<!-- 基本 Summary Card -->
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="網頁標題">
<meta name="twitter:description" content="網頁描述">
<meta name="twitter:image" content="https://example.com/image.jpg">

<!-- Summary Card with Large Image -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="HTML5 語意化標籤完整指南">
<meta name="twitter:description" content="深入了解 HTML5 所有語意化標籤">
<meta name="twitter:image" content="https://example.com/images/html5-guide.jpg">
<meta name="twitter:site" content="@mywebsite">
<meta name="twitter:creator" content="@authorname">

<!-- 完整範例（結合 Open Graph） -->
<!-- Open Graph 標籤 -->
<meta property="og:title" content="文章標題">
<meta property="og:description" content="文章描述">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com/article">

<!-- Twitter Card 標籤 -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@mysite">
<meta name="twitter:creator" content="@author">
<!-- Twitter 會自動使用 og: 標籤，不需重複 -->
```

#### Twitter Card 類型

| 類型 | 說明 | 圖片尺寸 |
|------|------|----------|
| `summary` | 小圖卡片 | 1:1（最小 144x144） |
| `summary_large_image` | 大圖卡片 | 2:1（最小 300x157） |
| `app` | App 卡片 | 應用程式資訊 |
| `player` | 播放器卡片 | 影片/音訊播放器 |

#### 使用注意事項

```html
<!-- ✅ 正確：結合使用 OG 和 Twitter -->
<meta property="og:title" content="標題">
<meta property="og:description" content="描述">
<meta property="og:image" content="https://example.com/image.jpg">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@mysite">

<!-- ✅ 簡化：Twitter 會使用 OG 標籤 -->
<!-- 只需要指定 card 類型 -->
<meta name="twitter:card" content="summary_large_image">
```

---

### theme-color - 主題顏色

#### 說明
定義瀏覽器工具列和系統 UI 的顏色（主要用於行動裝置）。

#### 📌 程式碼範例

```html
<!-- 基本用法 -->
<meta name="theme-color" content="#3b82f6">

<!-- 暗色主題 -->
<meta name="theme-color" content="#1e293b" media="(prefers-color-scheme: dark)">

<!-- 亮色主題 -->
<meta name="theme-color" content="#ffffff" media="(prefers-color-scheme: light)">

<!-- 多個主題顏色 -->
<meta name="theme-color" content="#ffffff" media="(prefers-color-scheme: light)">
<meta name="theme-color" content="#000000" media="(prefers-color-scheme: dark)">
```

#### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 39+ | ❌ | ✅ 15+ | ✅ 79+ | ❌ |

---

## `<link>` - 外部資源連結

### 說明
`<link>` 標籤定義當前文件與外部資源的關係，最常用於連結 CSS 樣式表。

### 語法
```html
<link rel="關係" href="URL">
```

### 常用屬性

| 屬性 | 說明 | 必需 |
|------|------|------|
| `rel` | 關係類型 | ✅ |
| `href` | 資源 URL | ✅ |
| `type` | 資源 MIME 類型 | ⚪ |
| `media` | 媒體查詢 | ⚪ |
| `sizes` | 圖示尺寸 | ⚪ |
| `as` | 資源類型（用於 preload） | ⚪ |
| `crossorigin` | CORS 設定 | ⚪ |
| `integrity` | SRI 完整性檢查 | ⚪ |

---

### stylesheet - 樣式表

#### 📌 程式碼範例

```html
<!-- 基本 CSS 連結 -->
<link rel="stylesheet" href="styles.css">

<!-- 指定 MIME 類型 -->
<link rel="stylesheet" href="styles.css" type="text/css">

<!-- 媒體查詢 -->
<link rel="stylesheet" href="print.css" media="print">
<link rel="stylesheet" href="mobile.css" media="screen and (max-width: 768px)">

<!-- 從 CDN 載入 -->
<link rel="stylesheet" href="https://cdn.example.com/bootstrap.min.css">

<!-- 帶完整性檢查的 CDN -->
<link rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
      integrity="sha384-..."
      crossorigin="anonymous">

<!-- 多個樣式表 -->
<link rel="stylesheet" href="reset.css">
<link rel="stylesheet" href="base.css">
<link rel="stylesheet" href="layout.css">
<link rel="stylesheet" href="components.css">
```

#### 媒體查詢範例

```html
<!-- 印刷樣式 -->
<link rel="stylesheet" href="print.css" media="print">

<!-- 螢幕樣式 -->
<link rel="stylesheet" href="screen.css" media="screen">

<!-- 響應式 -->
<link rel="stylesheet" href="mobile.css" media="(max-width: 768px)">
<link rel="stylesheet" href="tablet.css" media="(min-width: 769px) and (max-width: 1024px)">
<link rel="stylesheet" href="desktop.css" media="(min-width: 1025px)">

<!-- 暗色模式 -->
<link rel="stylesheet" href="dark.css" media="(prefers-color-scheme: dark)">
<link rel="stylesheet" href="light.css" media="(prefers-color-scheme: light)">
```

---

### icon - 網站圖示

#### 📌 程式碼範例

```html
<!-- 基本 favicon -->
<link rel="icon" href="/favicon.ico">

<!-- PNG favicon -->
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">

<!-- SVG favicon（現代瀏覽器） -->
<link rel="icon" type="image/svg+xml" href="/favicon.svg">

<!-- Apple Touch Icon -->
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">

<!-- Android Chrome -->
<link rel="icon" type="image/png" sizes="192x192" href="/android-chrome-192x192.png">
<link rel="icon" type="image/png" sizes="512x512" href="/android-chrome-512x512.png">

<!-- 完整圖示集 -->
<link rel="icon" type="image/x-icon" href="/favicon.ico">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="192x192" href="/android-chrome-192x192.png">
<link rel="icon" type="image/png" sizes="512x512" href="/android-chrome-512x512.png">
<link rel="manifest" href="/site.webmanifest">
```

#### 圖示尺寸建議

| 類型 | 尺寸 | 用途 |
|------|------|------|
| favicon.ico | 16x16, 32x32 | 瀏覽器標籤 |
| favicon.png | 16x16, 32x32 | 現代瀏覽器 |
| apple-touch-icon | 180x180 | iOS 主畫面 |
| android-chrome | 192x192, 512x512 | Android 主畫面 |

---

### preload/prefetch - 預載資源

#### 說明
`preload` 和 `prefetch` 用於優化資源載入效能。

#### 📌 程式碼範例

```html
<!-- preload: 預載當前頁面需要的關鍵資源 -->
<link rel="preload" href="styles.css" as="style">
<link rel="preload" href="script.js" as="script">
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="hero.jpg" as="image">

<!-- prefetch: 預載未來可能需要的資源 -->
<link rel="prefetch" href="next-page.html">
<link rel="prefetch" href="secondary.css">

<!-- preconnect: 預先連接到來源 -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- dns-prefetch: DNS 預解析 -->
<link rel="dns-prefetch" href="https://cdn.example.com">

<!-- modulepreload: 預載 ES 模組 -->
<link rel="modulepreload" href="app.js">
```

#### 資源類型（as 屬性）

| 類型 | 說明 |
|------|------|
| `style` | CSS 樣式表 |
| `script` | JavaScript |
| `font` | 字型檔案 |
| `image` | 圖片 |
| `fetch` | fetch/XHR 請求 |
| `document` | HTML 文件 |
| `audio` | 音訊檔案 |
| `video` | 視訊檔案 |

#### 使用場景

```html
<!-- ✅ preload: 關鍵資源（立即需要） -->
<link rel="preload" href="critical.css" as="style">
<link rel="preload" href="main-font.woff2" as="font" type="font/woff2" crossorigin>

<!-- ✅ prefetch: 下一頁資源（未來需要） -->
<link rel="prefetch" href="/page2.html">
<link rel="prefetch" href="/images/hero-next.jpg">

<!-- ✅ preconnect: 第三方來源 -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://www.google-analytics.com">
```

---

### canonical - 標準網址

#### 說明
指定頁面的標準（canonical）URL，避免重複內容問題。

#### 📌 程式碼範例

```html
<!-- 基本用法 -->
<link rel="canonical" href="https://example.com/page">

<!-- 避免重複內容 -->
<!-- 以下 URL 都指向同一個標準 URL -->
<!-- https://example.com/page -->
<!-- https://example.com/page?utm_source=facebook -->
<!-- https://example.com/page?ref=twitter -->
<!-- https://www.example.com/page -->

<link rel="canonical" href="https://example.com/page">

<!-- 分頁內容 -->
<link rel="canonical" href="https://example.com/article">
<!-- 在 /article?page=2, /article?page=3 等頁面上 -->
```

#### 使用場景

```html
<!-- ✅ 情況 1: 多個 URL 指向相同內容 -->
<!-- 在 https://example.com/product?color=red 上 -->
<link rel="canonical" href="https://example.com/product">

<!-- ✅ 情況 2: HTTP vs HTTPS -->
<!-- 在 http://example.com/page 上 -->
<link rel="canonical" href="https://example.com/page">

<!-- ✅ 情況 3: www vs non-www -->
<!-- 在 http://www.example.com/page 上 -->
<link rel="canonical" href="https://example.com/page">

<!-- ✅ 情況 4: 追蹤參數 -->
<!-- 在 https://example.com/page?utm_source=email 上 -->
<link rel="canonical" href="https://example.com/page">
```

---

### alternate - 替代版本

#### 說明
指定頁面的替代版本（如不同語言、行動版、RSS feed）。

#### 📌 程式碼範例

```html
<!-- 多語言版本 -->
<link rel="alternate" hreflang="zh-TW" href="https://example.com/tw/">
<link rel="alternate" hreflang="zh-CN" href="https://example.com/cn/">
<link rel="alternate" hreflang="en" href="https://example.com/en/">
<link rel="alternate" hreflang="ja" href="https://example.com/jp/">
<link rel="alternate" hreflang="x-default" href="https://example.com/">

<!-- RSS feed -->
<link rel="alternate" type="application/rss+xml" title="RSS Feed" href="/feed.xml">

<!-- Atom feed -->
<link rel="alternate" type="application/atom+xml" title="Atom Feed" href="/atom.xml">

<!-- AMP 版本 -->
<link rel="amphtml" href="https://example.com/amp/article">

<!-- 行動版（較少使用，建議響應式設計） -->
<link rel="alternate" media="only screen and (max-width: 640px)" href="https://m.example.com/">
```

---

## `<style>` - 內嵌樣式

### 說明
`<style>` 標籤在 HTML 文件中定義 CSS 樣式。

### 語法
```html
<style>
  CSS 樣式規則
</style>
```

### 常用屬性

| 屬性 | 說明 | 必需 |
|------|------|------|
| `type` | MIME 類型 | ⚪（預設 text/css） |
| `media` | 媒體查詢 | ⚪ |

### 📌 程式碼範例

```html
<!-- 基本內嵌樣式 -->
<style>
  body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
  }

  h1 {
    color: #333;
  }
</style>

<!-- 針對特定媒體 -->
<style media="print">
  body {
    font-size: 12pt;
    color: black;
  }

  .no-print {
    display: none;
  }
</style>

<!-- 暗色模式 -->
<style media="(prefers-color-scheme: dark)">
  body {
    background-color: #1a1a1a;
    color: #ffffff;
  }
</style>

<!-- Critical CSS（關鍵 CSS） -->
<style>
  /* 首屏關鍵樣式 */
  .header {
    background: #007bff;
    padding: 1rem;
  }

  .hero {
    min-height: 400px;
    display: flex;
    align-items: center;
  }
</style>

<!-- 其餘樣式延遲載入 -->
<link rel="preload" href="main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="main.css"></noscript>
```

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項

```html
<!-- ✅ 正確：用於 Critical CSS -->
<style>
  /* 首屏必要樣式 */
  .hero { ... }
</style>
<link rel="stylesheet" href="main.css">

<!-- ⚠️ 避免：大量內嵌樣式 -->
<style>
  /* 數千行 CSS... */
  /* 應該使用外部 CSS 檔案 */
</style>

<!-- ❌ 錯誤：在 body 中使用 style -->
<body>
  <style>...</style> <!-- 應該在 head 中 -->
</body>

<!-- ✅ 正確：在 head 中 -->
<head>
  <style>...</style>
</head>
```

---

## `<script>` - JavaScript

### 說明
`<script>` 標籤用於嵌入或引用 JavaScript 程式碼。

### 語法
```html
<!-- 外部 JavaScript -->
<script src="URL"></script>

<!-- 內嵌 JavaScript -->
<script>
  JavaScript 程式碼
</script>
```

### 常用屬性

| 屬性 | 說明 | 值 |
|------|------|-----|
| `src` | 外部腳本 URL | URL |
| `type` | 腳本類型 | `text/javascript`, `module` |
| `async` | 非同步載入 | 布林值 |
| `defer` | 延遲執行 | 布林值 |
| `crossorigin` | CORS 設定 | `anonymous`, `use-credentials` |
| `integrity` | SRI 完整性檢查 | 雜湊值 |
| `nomodule` | 舊瀏覽器降級 | 布林值 |

### 📌 程式碼範例

```html
<!-- 基本外部腳本 -->
<script src="script.js"></script>

<!-- 內嵌腳本 -->
<script>
  console.log('Hello, World!');
  document.addEventListener('DOMContentLoaded', function() {
    // 初始化程式碼
  });
</script>

<!-- 從 CDN 載入 -->
<script src="https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js"></script>

<!-- 帶完整性檢查 -->
<script
  src="https://code.jquery.com/jquery-3.6.0.min.js"
  integrity="sha256-..."
  crossorigin="anonymous"></script>
```

---

### defer - 延遲執行

#### 說明
`defer` 屬性讓腳本在 HTML 解析完成後才執行，但保持執行順序。

#### 📌 程式碼範例

```html
<!-- 使用 defer -->
<script src="script1.js" defer></script>
<script src="script2.js" defer></script>
<script src="script3.js" defer></script>

<!-- 執行順序：script1 → script2 → script3 -->
<!-- 在 DOMContentLoaded 之前執行 -->
```

#### 執行時機

```
HTML 解析開始
↓
遇到 <script defer> → 背景下載，繼續解析
↓
HTML 解析完成
↓
執行所有 defer 腳本（按順序）
↓
觸發 DOMContentLoaded 事件
```

---

### async - 非同步載入

#### 說明
`async` 屬性讓腳本非同步載入和執行，不保證執行順序。

#### 📌 程式碼範例

```html
<!-- 使用 async -->
<script src="analytics.js" async></script>
<script src="ads.js" async></script>

<!-- 執行順序：不確定（誰先載入完成誰先執行） -->
```

#### 執行時機

```
HTML 解析開始
↓
遇到 <script async> → 背景下載，繼續解析
↓
腳本下載完成 → 立即執行（暫停 HTML 解析）
↓
繼續 HTML 解析
```

---

### defer vs async 比較

| 特性 | 無屬性 | defer | async |
|------|--------|-------|-------|
| 載入 | 同步（阻塞） | 非同步 | 非同步 |
| 執行時機 | 立即 | HTML 解析後 | 載入完成後 |
| 執行順序 | ✅ 保證 | ✅ 保證 | ❌ 不保證 |
| 阻塞解析 | ✅ 會 | ❌ 不會 | ⚠️ 執行時會 |
| DOMContentLoaded | 等待腳本 | 等待腳本 | 不等待 |

#### 使用建議

```html
<!-- ✅ defer: 一般腳本（推薦） -->
<script src="main.js" defer></script>
<script src="components.js" defer></script>

<!-- ✅ async: 獨立腳本（分析、廣告） -->
<script src="analytics.js" async></script>
<script src="ads.js" async></script>

<!-- ❌ 無屬性: 阻塞渲染（避免） -->
<script src="script.js"></script>

<!-- ✅ 放在 body 結尾（替代方案） -->
<body>
  <!-- 內容 -->
  <script src="script.js"></script>
</body>
```

---

### module - ES 模組

#### 說明
`type="module"` 讓瀏覽器將腳本視為 ES6 模組。

#### 📌 程式碼範例

```html
<!-- ES 模組 -->
<script type="module" src="app.js"></script>

<!-- 內嵌模組 -->
<script type="module">
  import { hello } from './utils.js';
  hello();
</script>

<!-- 舊瀏覽器降級 -->
<script type="module" src="modern.js"></script>
<script nomodule src="legacy.js"></script>

<!-- 預載模組 -->
<link rel="modulepreload" href="app.js">
<link rel="modulepreload" href="utils.js">
```

#### 模組特性

- 自動使用 `defer`
- 自動使用嚴格模式（`"use strict"`）
- 有自己的作用域
- 支援 `import` / `export`

---

## `<base>` - 基準 URL

### 說明
`<base>` 定義頁面中所有相對 URL 的基準 URL。

### 語法
```html
<base href="基準URL" target="目標">
```

### 常用屬性

| 屬性 | 說明 | 必需 |
|------|------|------|
| `href` | 基準 URL | ⚪ |
| `target` | 預設目標 | ⚪ |

### 📌 程式碼範例

```html
<!-- 基本用法 -->
<head>
  <base href="https://example.com/">
  <!-- 所有相對 URL 都基於此 -->
</head>
<body>
  <!-- 實際指向 https://example.com/page.html -->
  <a href="page.html">連結</a>

  <!-- 實際指向 https://example.com/images/logo.png -->
  <img src="images/logo.png" alt="Logo">
</body>

<!-- 設定預設目標 -->
<base href="https://example.com/" target="_blank">
<!-- 所有連結預設在新視窗開啟 -->

<!-- 子目錄基準 -->
<base href="https://example.com/blog/">
<!-- images/photo.jpg → https://example.com/blog/images/photo.jpg -->
```

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項

```html
<!-- ✅ 正確：在 head 中，且只有一個 -->
<head>
  <base href="https://example.com/">
</head>

<!-- ❌ 錯誤：多個 base（只有第一個生效） -->
<base href="https://example.com/">
<base href="https://other.com/"> <!-- 無效 -->

<!-- ⚠️ 注意：影響所有相對 URL -->
<base href="https://example.com/products/">
<!-- /about → https://example.com/about（絕對路徑不受影響） -->
<!-- about → https://example.com/products/about（相對路徑會受影響） -->

<!-- ⚠️ 注意：也影響錨點連結 -->
<base href="https://example.com/">
<a href="#section">跳到區段</a>
<!-- 實際上會導向 https://example.com/#section -->
```

---

## `<noscript>` - JavaScript 替代內容

### 說明
`<noscript>` 標籤定義在瀏覽器不支援或停用 JavaScript 時顯示的內容。

### 語法
```html
<noscript>
  替代內容
</noscript>
```

### 📌 程式碼範例

```html
<!-- 基本用法 -->
<noscript>
  <p>您的瀏覽器不支援 JavaScript，部分功能可能無法正常運作。</p>
</noscript>

<!-- 提供替代連結 -->
<noscript>
  <p>請<a href="/nojs-version">點此</a>使用無 JavaScript 版本。</p>
</noscript>

<!-- 載入替代樣式 -->
<noscript>
  <link rel="stylesheet" href="noscript.css">
</noscript>

<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>
<noscript>
  <iframe src="https://www.googletagmanager.com/ns.html?id=GTM-XXXX"
          height="0" width="0" style="display:none;visibility:hidden"></iframe>
</noscript>

<!-- 延遲載入 CSS 的降級方案 -->
<link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript>
  <link rel="stylesheet" href="styles.css">
</noscript>

<!-- 完整範例 -->
<head>
  <script>
    // 檢測 JavaScript 啟用
    document.documentElement.className = 'js-enabled';
  </script>
  <noscript>
    <style>
      .js-only {
        display: none;
      }
      .no-js-message {
        display: block;
        background: #fff3cd;
        padding: 1rem;
        text-align: center;
      }
    </style>
  </noscript>
</head>
<body>
  <noscript>
    <div class="no-js-message">
      <strong>注意：</strong>
      本網站需要 JavaScript 才能正常運作。
      請啟用 JavaScript 或使用支援的瀏覽器。
    </div>
  </noscript>

  <div class="js-only">
    <!-- 需要 JavaScript 的內容 -->
  </div>
</body>
```

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項

```html
<!-- ✅ 正確：提供有用的資訊 -->
<noscript>
  <p>本網站需要 JavaScript。請啟用後重新載入頁面。</p>
</noscript>

<!-- ⚠️ 過度：不需要每個腳本都加 noscript -->
<script src="script1.js"></script>
<noscript>script1 需要 JS</noscript> <!-- 不必要 -->
<script src="script2.js"></script>
<noscript>script2 需要 JS</noscript> <!-- 不必要 -->

<!-- ✅ 正確：在 head 中一次性說明 -->
<head>
  <noscript>
    <meta http-equiv="refresh" content="0; url=/no-js">
  </noscript>
</head>
```

---

## 完整 Head 範例

### 基本網站

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <!-- 字元編碼 -->
  <meta charset="UTF-8">

  <!-- 視口設定 -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- 標題 -->
  <title>網站標題 - 網站名稱</title>

  <!-- SEO -->
  <meta name="description" content="網站描述，150-160 字元">
  <meta name="author" content="作者名稱">

  <!-- 網站圖示 -->
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">

  <!-- CSS -->
  <link rel="stylesheet" href="/css/main.css">

  <!-- JavaScript -->
  <script src="/js/main.js" defer></script>
</head>
```

### 完整範例（部落格文章）

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <!-- ========== 基本設定 ========== -->
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">

  <!-- ========== 標題和描述 ========== -->
  <title>HTML5 語意化標籤完整指南 - 我的技術部落格</title>
  <meta name="description" content="深入了解 HTML5 所有語意化標籤的使用方法、最佳實踐和實際應用範例。適合網頁開發者學習參考。">
  <meta name="author" content="張三">

  <!-- ========== SEO ========== -->
  <meta name="robots" content="index, follow">
  <link rel="canonical" href="https://example.com/blog/html5-semantic-tags">

  <!-- ========== Open Graph (Facebook, LinkedIn) ========== -->
  <meta property="og:type" content="article">
  <meta property="og:title" content="HTML5 語意化標籤完整指南">
  <meta property="og:description" content="深入了解 HTML5 所有語意化標籤的使用方法和最佳實踐">
  <meta property="og:image" content="https://example.com/images/html5-guide-og.jpg">
  <meta property="og:image:width" content="1200">
  <meta property="og:image:height" content="630">
  <meta property="og:url" content="https://example.com/blog/html5-semantic-tags">
  <meta property="og:site_name" content="我的技術部落格">
  <meta property="og:locale" content="zh_TW">
  <meta property="article:published_time" content="2026-01-02T14:30:00+08:00">
  <meta property="article:author" content="張三">
  <meta property="article:section" content="網頁開發">
  <meta property="article:tag" content="HTML5">
  <meta property="article:tag" content="語意化">
  <meta property="article:tag" content="網頁開發">

  <!-- ========== Twitter Card ========== -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:site" content="@myblog">
  <meta name="twitter:creator" content="@zhangsan">

  <!-- ========== 網站圖示 ========== -->
  <link rel="icon" type="image/x-icon" href="/favicon.ico">
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
  <link rel="icon" type="image/png" sizes="192x192" href="/android-chrome-192x192.png">
  <link rel="manifest" href="/site.webmanifest">

  <!-- ========== 主題顏色 ========== -->
  <meta name="theme-color" content="#3b82f6" media="(prefers-color-scheme: light)">
  <meta name="theme-color" content="#1e293b" media="(prefers-color-scheme: dark)">

  <!-- ========== 多語言版本 ========== -->
  <link rel="alternate" hreflang="zh-TW" href="https://example.com/tw/blog/html5-semantic-tags">
  <link rel="alternate" hreflang="en" href="https://example.com/en/blog/html5-semantic-tags">
  <link rel="alternate" hreflang="x-default" href="https://example.com/blog/html5-semantic-tags">

  <!-- ========== RSS Feed ========== -->
  <link rel="alternate" type="application/rss+xml" title="RSS Feed" href="/feed.xml">

  <!-- ========== 預連接 ========== -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link rel="dns-prefetch" href="https://www.google-analytics.com">

  <!-- ========== CSS ========== -->
  <!-- Critical CSS -->
  <style>
    /* 首屏關鍵樣式 */
    body { margin: 0; font-family: system-ui, -apple-system, sans-serif; }
    .header { background: #3b82f6; color: white; padding: 1rem; }
  </style>

  <!-- 預載字型 -->
  <link rel="preload" href="/fonts/main-font.woff2" as="font" type="font/woff2" crossorigin>

  <!-- 外部樣式表 -->
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;700&display=swap">
  <link rel="stylesheet" href="/css/main.css">
  <link rel="stylesheet" href="/css/syntax-highlight.css">

  <!-- 印刷樣式 -->
  <link rel="stylesheet" href="/css/print.css" media="print">

  <!-- ========== JavaScript ========== -->
  <!-- 分析工具 -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'GA_TRACKING_ID');
  </script>

  <!-- 主要腳本 -->
  <script src="/js/main.js" defer></script>

  <!-- ========== 結構化資料 (JSON-LD) ========== -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    "headline": "HTML5 語意化標籤完整指南",
    "image": "https://example.com/images/html5-guide.jpg",
    "author": {
      "@type": "Person",
      "name": "張三",
      "url": "https://example.com/author/zhangsan"
    },
    "publisher": {
      "@type": "Organization",
      "name": "我的技術部落格",
      "logo": {
        "@type": "ImageObject",
        "url": "https://example.com/logo.png"
      }
    },
    "datePublished": "2026-01-02T14:30:00+08:00",
    "dateModified": "2026-01-02T16:00:00+08:00",
    "description": "深入了解 HTML5 所有語意化標籤的使用方法和最佳實踐"
  }
  </script>

  <!-- ========== noscript ========== -->
  <noscript>
    <link rel="stylesheet" href="/css/noscript.css">
  </noscript>
</head>
```

---

## SEO 優化指南

### 1. 必備 Meta 標籤

```html
<!-- ✅ 最重要的 5 個 -->
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>頁面標題 - 網站名稱</title>
<meta name="description" content="150-160 字元的描述">
<link rel="canonical" href="https://example.com/page">
```

### 2. 標題優化

```html
<!-- ✅ 正確：描述性、包含關鍵字、不超過 60 字元 -->
<title>HTML5 語意化標籤教學 - 網頁開發指南</title>

<!-- ❌ 錯誤：過短 -->
<title>首頁</title>

<!-- ❌ 錯誤：過長（會被截斷） -->
<title>HTML5 語意化標籤完整教學包含所有標籤說明範例最佳實踐 SEO 優化無障礙設計...</title>

<!-- ❌ 錯誤：關鍵字堆砌 -->
<title>HTML, HTML5, 網頁, 網頁設計, 網頁開發, 前端, 教學</title>
```

### 3. Open Graph 優化

```html
<!-- ✅ 完整的 OG 標籤 -->
<meta property="og:title" content="吸引人的標題">
<meta property="og:description" content="簡潔的描述">
<meta property="og:image" content="https://example.com/image-1200x630.jpg">
<meta property="og:url" content="https://example.com/page">
<meta property="og:type" content="article">
```

### 4. 結構化資料

```html
<!-- JSON-LD 結構化資料 -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "文章標題",
  "author": {
    "@type": "Person",
    "name": "作者名稱"
  },
  "datePublished": "2026-01-02"
}
</script>
```

---

## 效能優化指南

### 1. CSS 載入優化

```html
<!-- ❌ 阻塞：多個樣式表 -->
<link rel="stylesheet" href="style1.css">
<link rel="stylesheet" href="style2.css">
<link rel="stylesheet" href="style3.css">

<!-- ✅ 優化：Critical CSS + 延遲載入 -->
<style>
  /* Critical CSS（首屏樣式） */
</style>
<link rel="preload" href="main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="main.css"></noscript>
```

### 2. JavaScript 載入優化

```html
<!-- ❌ 阻塞：同步載入 -->
<script src="large-library.js"></script>

<!-- ✅ 優化：defer/async -->
<script src="main.js" defer></script>
<script src="analytics.js" async></script>
```

### 3. 字型載入優化

```html
<!-- ✅ 預載關鍵字型 -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="preload" href="/fonts/main-font.woff2" as="font" type="font/woff2" crossorigin>

<!-- ✅ 使用 font-display -->
<style>
  @font-face {
    font-family: 'MyFont';
    src: url('/fonts/myfont.woff2') format('woff2');
    font-display: swap; /* 或 optional, fallback */
  }
</style>
```

### 4. 資源提示

```html
<!-- 預連接到重要來源 -->
<link rel="preconnect" href="https://cdn.example.com">

<!-- DNS 預解析 -->
<link rel="dns-prefetch" href="https://analytics.example.com">

<!-- 預載關鍵資源 -->
<link rel="preload" href="critical.css" as="style">
<link rel="preload" href="hero.jpg" as="image">

<!-- 預取下一頁資源 -->
<link rel="prefetch" href="/page2.html">
```

---

## 最佳實踐總結

### ✅ 必須做的事

1. **基本設定**
   - 總是使用 `<meta charset="UTF-8">`
   - 總是使用 viewport meta 標籤
   - 提供有意義的 `<title>`
   - 提供準確的 `<meta name="description">`

2. **SEO 優化**
   - 使用 canonical URL
   - 提供 Open Graph 標籤
   - 每個頁面有獨特的 title 和 description
   - 使用結構化資料（JSON-LD）

3. **效能優化**
   - CSS 使用 preload 或 Critical CSS
   - JavaScript 使用 defer 或 async
   - 預連接到第三方來源
   - 優化字型載入

4. **無障礙性**
   - 提供 `lang` 屬性
   - 提供多語言替代版本（如有）
   - 不禁止使用者縮放（viewport）

5. **安全性**
   - 使用 HTTPS
   - CDN 資源使用 integrity 檢查
   - 考慮使用 CSP（Content Security Policy）

### ❌ 避免的事

1. **錯誤設定**
   - ❌ 忘記 charset（導致亂碼）
   - ❌ 沒有 viewport（行動版體驗差）
   - ❌ 標題過短或重複
   - ❌ 沒有 description

2. **效能問題**
   - ❌ 大量同步 JavaScript
   - ❌ 沒有優化 CSS 載入
   - ❌ 沒有使用資源提示
   - ❌ 載入過大的第三方庫

3. **SEO 問題**
   - ❌ 關鍵字堆砌
   - ❌ 重複內容沒有 canonical
   - ❌ 缺少 Open Graph 標籤
   - ❌ 圖片沒有 alt（雖然不在 meta，但很重要）

4. **安全問題**
   - ❌ HTTP 載入資源（混合內容）
   - ❌ CDN 沒有 integrity 檢查
   - ❌ 沒有 CSP 保護

### 🎯 進階優化

1. **效能監控**
   - 使用 Lighthouse 評分
   - 監控 Core Web Vitals
   - 優化 LCP、FID、CLS

2. **進階 SEO**
   - 實作麵包屑結構化資料
   - 使用 hreflang 支援多語言
   - 提供 RSS feed
   - 使用 AMP（如適用）

3. **PWA 支援**
   - 提供 manifest.json
   - 使用 Service Worker
   - 支援離線功能

4. **國際化**
   - 提供多語言版本
   - 使用正確的 hreflang
   - 考慮 RTL 語言支援

---

**記住**: Meta 標籤雖然不可見，但對 SEO、社群分享、效能和使用者體驗都有重大影響。花時間正確設定這些標籤是值得的投資！

---

[⬆️ 回到頂部](#元數據標籤-metadata-elements) | [📑 回索引頁](index.md)
