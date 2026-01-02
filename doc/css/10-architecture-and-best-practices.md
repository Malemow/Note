# 10. CSS 架構與最佳實踐 (Architecture & Best Practices)

學會語法後，下一步是學習如何寫出「可維護」且「具包容性」的 CSS。

## 1. BEM 命名規範 (Block Element Modifier)

在沒有 Scoped CSS (如 CSS Modules, Vue Scoped) 的環境下，BEM 是防止樣式衝突的業界標準。

### 格式
`block__element--modifier`

- **Block (區塊)**: 獨立的元件 (如 `.card`, `.navbar`)。
- **Element (元素)**: 區塊內的組成部分，依賴於區塊 (如 `.card__title`, `.navbar__item`)。
- **Modifier (修飾符)**: 狀態或變體 (如 `.card--featured`, `.btn--disabled`)。

### 範例
```css
/* Bad: 容易污染全域，且看不出關係 */
.card {}
.title {}
.active {}

/* Good (BEM): 結構清晰，不會互相影響 */
.card {}
.card__title {}
.card__button {}
.card__button--primary {} /* 變體 */
.card--active {}          /* 狀態 */
```

---

## 2. 主題化架構 (Theming Strategy)

不要在每個元件裡寫死顏色 (Hard-coded values)。應該定義「語意化」的變數。

### 第一層：原始色盤 (Primitives)
定義品牌色、灰階等基礎數值。
```css
:root {
  --gray-900: #1a202c;
  --gray-100: #f7fafc;
  --blue-500: #3182ce;
}
```

### 第二層：語意化變數 (Semantic Tokens)
定義「用途」，並在不同主題下改變這些變數的值。
```css
:root {
  --text-primary: var(--gray-900);
  --bg-surface: var(--gray-100);
  --btn-bg: var(--blue-500);
}

/* 深色模式：只需要覆蓋「語意變數」 */
[data-theme="dark"] {
  --text-primary: var(--gray-100);
  --bg-surface: var(--gray-900);
}
```

---

## 3. 無障礙與隱藏 (Accessibility & Hiding)

### 正確隱藏元素 (`.sr-only`)
有時候我們需要隱藏標籤文字（例如 Icon Button），但希望螢幕閱讀器讀得出來。
**千萬不要用 `display: none` (螢幕閱讀器會忽略)。**

```css
/* Screen Reader Only: 視覺看不見，但 DOM 仍存在且可被報讀 */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

### Focus 可見性
永遠不要移除 `:focus` 的 outline，除非你有自定義的替代樣式。
```css
/* Bad: 鍵盤使用者會迷路 */
button:focus { outline: none; }

/* Good: 使用 focus-visible 只在鍵盤操作時顯示焦點 */
button:focus:not(:focus-visible) { outline: none; }
button:focus-visible { outline: 2px solid blue; }
```
