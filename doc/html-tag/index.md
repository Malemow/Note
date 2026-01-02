# HTML Tags 完整教學指南

> 符合 W3C 規範的 HTML 標籤完整參考文件

## 📚 關於本教學

本教學涵蓋所有 HTML5 標準標籤，包含詳細說明、屬性、範例、瀏覽器支援度及最佳實踐。所有內容均符合 **W3C (World Wide Web Consortium)** 最新規範。

### W3C 規範說明

W3C 是制定網頁標準的國際組織，確保網頁在不同瀏覽器和設備上都能正確顯示。本教學遵循：

- **HTML5 Living Standard** - 由 WHATWG 維護的 HTML 標準
- **W3C HTML 5.3 Recommendation** - W3C 官方推薦標準
- **WCAG 2.1** - 網頁內容無障礙指南

---

## 🗂️ 標籤分類導航

### 1. [基本結構標籤](basic-structure.md)
文件的基礎架構標籤
- `<!DOCTYPE>`, `<html>`, `<head>`, `<body>`, `<title>` 等

### 2. [文字內容標籤](text-content.md)
文字排版與內容呈現
- `<h1>-<h6>`, `<p>`, `<div>`, `<span>`, `<strong>`, `<em>` 等

### 3. [列表標籤](lists.md)
各種列表結構
- `<ul>`, `<ol>`, `<li>`, `<dl>`, `<dt>`, `<dd>` 等

### 4. [表格標籤](tables.md)
表格資料呈現
- `<table>`, `<tr>`, `<td>`, `<th>`, `<thead>`, `<tbody>`, `<tfoot>` 等

### 5. [表單標籤](forms.md)
使用者輸入與互動表單
- `<form>`, `<input>`, `<select>`, `<textarea>`, `<button>`, `<label>` 等

### 6. [多媒體標籤](media.md)
圖片、音訊、視訊等多媒體內容
- `<img>`, `<audio>`, `<video>`, `<picture>`, `<source>`, `<track>` 等

### 7. [語意化標籤](semantic.md)
HTML5 語意化結構標籤
- `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>` 等

### 8. [元數據標籤](metadata.md)
文件頭部資訊與設定
- `<meta>`, `<link>`, `<style>`, `<script>`, `<base>`, `<noscript>` 等

### 9. [互動元素標籤](interactive.md)
互動性元素與組件
- `<a>`, `<button>`, `<details>`, `<summary>`, `<dialog>`, `<menu>` 等

### 10. [嵌入內容標籤](embedded.md)
外部內容嵌入
- `<iframe>`, `<embed>`, `<object>`, `<param>`, `<portal>` 等

### 11. [已廢棄標籤](deprecated.md)
不建議使用的標籤及其替代方案
- `<font>`, `<center>`, `<marquee>`, `<blink>`, `<frame>` 等

---

## 🔍 快速查詢表

### 最常用標籤（Top 20）

| 標籤 | 用途 | 分類 |
|------|------|------|
| `<div>` | 區塊容器 | [文字內容](text-content.md#div) |
| `<span>` | 行內容器 | [文字內容](text-content.md#span) |
| `<p>` | 段落 | [文字內容](text-content.md#p) |
| `<a>` | 超連結 | [互動元素](interactive.md#a) |
| `<img>` | 圖片 | [多媒體](media.md#img) |
| `<h1>-<h6>` | 標題 | [文字內容](text-content.md#h1-h6) |
| `<ul>` | 無序列表 | [列表](lists.md#ul) |
| `<ol>` | 有序列表 | [列表](lists.md#ol) |
| `<li>` | 列表項目 | [列表](lists.md#li) |
| `<form>` | 表單 | [表單](forms.md#form) |
| `<input>` | 輸入欄位 | [表單](forms.md#input) |
| `<button>` | 按鈕 | [表單](forms.md#button) |
| `<table>` | 表格 | [表格](tables.md#table) |
| `<header>` | 頁首 | [語意化](semantic.md#header) |
| `<footer>` | 頁尾 | [語意化](semantic.md#footer) |
| `<nav>` | 導航 | [語意化](semantic.md#nav) |
| `<section>` | 章節 | [語意化](semantic.md#section) |
| `<article>` | 文章 | [語意化](semantic.md#article) |
| `<script>` | 腳本 | [元數據](metadata.md#script) |
| `<style>` | 樣式 | [元數據](metadata.md#style) |

### 依功能分類

#### 文字格式化
`<strong>`, `<em>`, `<b>`, `<i>`, `<u>`, `<s>`, `<mark>`, `<small>`, `<sub>`, `<sup>`, `<code>`, `<pre>`, `<kbd>`, `<samp>`, `<var>`, `<abbr>`, `<cite>`, `<q>`, `<blockquote>`

#### 表單元素
`<form>`, `<input>`, `<textarea>`, `<select>`, `<option>`, `<optgroup>`, `<button>`, `<label>`, `<fieldset>`, `<legend>`, `<datalist>`, `<output>`, `<progress>`, `<meter>`

#### 多媒體
`<img>`, `<audio>`, `<video>`, `<picture>`, `<source>`, `<track>`, `<svg>`, `<canvas>`, `<figure>`, `<figcaption>`

#### 表格
`<table>`, `<tr>`, `<td>`, `<th>`, `<thead>`, `<tbody>`, `<tfoot>`, `<col>`, `<colgroup>`, `<caption>`

---

## 📖 學習建議

### 初學者路徑
1. 從 [基本結構標籤](basic-structure.md) 開始，了解 HTML 文件架構
2. 學習 [文字內容標籤](text-content.md)，掌握基本排版
3. 熟悉 [列表標籤](lists.md) 和 [表格標籤](tables.md)
4. 進階到 [表單標籤](forms.md) 和 [多媒體標籤](media.md)
5. 最後學習 [語意化標籤](semantic.md)，提升網頁品質

### 中級開發者
- 重點學習 [語意化標籤](semantic.md) 以改善 SEO 和無障礙性
- 深入研究 [表單標籤](forms.md) 的進階功能
- 了解 [元數據標籤](metadata.md) 優化網頁效能

### 進階開發者
- 研究各標籤的無障礙最佳實踐
- 學習瀏覽器相容性處理
- 查看 [已廢棄標籤](deprecated.md) 進行代碼遷移

---

## 🌐 官方資源連結

- [W3C HTML 官方規範](https://www.w3.org/TR/html/)
- [WHATWG HTML Living Standard](https://html.spec.whatwg.org/)
- [MDN Web Docs](https://developer.mozilla.org/zh-TW/docs/Web/HTML)
- [Can I Use - 瀏覽器支援查詢](https://caniuse.com/)
- [W3C Validator - HTML 驗證工具](https://validator.w3.org/)

---

## 📝 使用說明

### 圖示說明
- ✅ 建議使用
- ⚠️ 需注意相容性
- ❌ 已廢棄不建議使用
- 🆕 HTML5 新增

### 瀏覽器圖示
- 🌐 Chrome
- 🦊 Firefox
- 🧭 Safari
- 🔷 Edge
- 📱 Mobile

---

## 💡 最佳實踐提示

1. **語意化優先** - 使用最適合內容的標籤，而非僅用 `<div>` 和 `<span>`
2. **無障礙設計** - 正確使用 ARIA 屬性和語意標籤
3. **W3C 驗證** - 定期使用 W3C Validator 檢查 HTML
4. **避免廢棄標籤** - 參考 [已廢棄標籤](deprecated.md) 使用現代替代方案
5. **行動優先** - 考慮行動裝置的顯示和互動

---

## 📊 統計資訊

- **HTML5 標準標籤**: 約 110+ 個
- **常用標籤**: 約 30-40 個
- **已廢棄標籤**: 約 20+ 個
- **HTML5 新增**: 約 30+ 個

---

**最後更新**: 2026-01-02
**版本**: 1.0
**符合規範**: W3C HTML5, WHATWG HTML Living Standard

---

[⬆️ 回到頂部](#html-tags-完整教學指南)
