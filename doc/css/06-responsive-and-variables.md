# 06. 響應式設計與變數 (Responsive & Variables)

## 1. 媒體查詢 (Media Queries)

根據設備特性 (如寬度) 套用不同的 CSS。

### 語法
```css
/* 手機版優先 (Mobile First) 的寫法 */
.container {
  width: 100%;
}

/* 當螢幕寬度 >= 768px (平板/桌面) 時 */
@media (min-width: 768px) {
  .container {
    width: 750px;
  }
}

/* 當螢幕寬度 >= 1024px 時 */
@media (min-width: 1024px) {
  .container {
    width: 960px;
  }
}
```

### 常見斷點 (Breakpoints)
- `< 576px`: 手機 (直向)
- `>= 576px`: 手機 (橫向) / 小平板
- `>= 768px`: 平板
- `>= 992px`: 桌面電腦
- `>= 1200px`: 大型螢幕

## 2. CSS 變數 (Custom Properties)

CSS 變數允許在一個地方定義值，並在多處重複使用，支援動態修改 (透過 JS)。

### 定義與使用
通常定義在 `:root` (全域) 中。

```css
:root {
  --primary-color: #3498db;
  --spacing-unit: 16px;
  --font-stack: 'Roboto', sans-serif;
}

.button {
  color: var(--primary-color);
  padding: var(--spacing-unit);
  font-family: var(--font-stack);
}

/* 局部變數 (只在該選擇器內有效) */
.card {
  --card-bg: #fff;
  background: var(--card-bg);
}
```

## 3. 數學函數 (Math Functions)

現代 CSS 支援強大的計算功能。

- **`calc()`**: 計算數值 (支援混用單位)。
    - `width: calc(100% - 20px);`
- **`min()`**: 取最小值。
    - `width: min(500px, 100%);` (最寬 500px，但在小螢幕時為 100%)
- **`max()`**: 取最大值。
- **`clamp()`**: 區間限制 (最小值, 理想值, 最大值)。
    - `font-size: clamp(1rem, 2.5vw, 2rem);` (字體隨視窗縮放，但不小於 1rem 也不大於 2rem)

## 4. 容器查詢 (Container Queries) - *New*

不同於 Media Queries 偵測「視窗」大小，Container Queries 偵測「父容器」大小。

```css
.card-container {
  container-type: inline-size;
  container-name: card;
}

@container card (min-width: 400px) {
  .card-title {
    font-size: 2rem; /* 當父容器 > 400px 時變大 */
  }
}
```
