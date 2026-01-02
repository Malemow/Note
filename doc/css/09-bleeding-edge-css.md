# 09. 前沿 CSS 技術 (Bleeding Edge CSS: Houdini & Anchors)

這份文件介紹瀏覽器最新的 CSS 能力，包含 CSS Houdini 的變數類型定義與原生的錨點定位。

## 1. 自定義屬性類型：`@property` (CSS Houdini)

你提到的「自己定義 CSS 屬性」正是指這個。預設情況下，瀏覽器將 CSS 變數 `--my-var` 視為字串。

### 為什麼需要它？
試想你想對 `conic-gradient` (圓錐漸層) 做旋轉動畫：

```css
/* ❌ 無效：瀏覽器無法對 background-image 的內部字串做插值計算 */
div {
  background: conic-gradient(from var(--angle), red, blue);
  transition: --angle 1s; /* 瀏覽器不知道 --angle 是角度 */
}
```

### 使用 `@property` 賦予變數靈魂
我們可以告訴瀏覽器：「嘿！這個變數是一個 `<angle>` (角度)！」

```css
@property --angle {
  syntax: '<angle>';       /* 定義類型 */
  initial-value: 0deg;     /* 初始值 */
  inherits: false;         /* 是否繼承 */
}

/* ✅ 現在有效了！瀏覽器知道 0deg 到 360deg 中間的數值 */
@keyframes spin {
  to { --angle: 360deg; }
}

.card {
  background: conic-gradient(from var(--angle), red, blue);
  animation: spin 2s linear infinite;
}
```

---

## 2. 錨點定位：`anchor()` (Anchor Positioning)

*注意：目前主要支援於 Chrome/Edge 125+*

以前要做一個 Tooltip 跟隨按鈕，必須用 JavaScript (如 Popper.js) 計算 `top/left`。現在 CSS 原生支援！

### 核心概念
1.  **Anchor**: 定義參考點 (按鈕)。
2.  **Target**: 定義要定位的元素 (Tooltip)。

```css
/* 1. 定義錨點 */
.button {
  anchor-name: --my-tooltip-anchor;
}

/* 2. 連接並定位 */
.tooltip {
  position: absolute;
  position-anchor: --my-tooltip-anchor; /* 綁定錨點 */
  
  /* 使用 anchor() 函數 */
  top: anchor(bottom);    /* Tooltip 頂部貼齊 Anchor 底部 */
  left: anchor(center);   /* Tooltip 左邊貼齊 Anchor 中間 */
  transform: translateX(-50%); /* 修正自身置中 */
}
```

---

## 3. 視圖過渡：View Transitions API (JS + CSS)

這是一個「JS 觸發，CSS 執行」的強大 API。當 DOM 發生劇烈變化（例如排序列表、換頁）時，它會自動抓取變化前與變化後的快照，並產生淡入淡出或移動效果。

### 語法
```javascript
// 通知瀏覽器：我要改變 DOM 了，請幫我做過渡動畫
document.startViewTransition(() => {
  // 這裡執行實際的 DOM 修改
  updateDOM(); 
});
```

### CSS 自定義
```css
/* 預設是淡入淡出 (cross-fade)，你可以自訂動畫 */
::view-transition-old(root),
::view-transition-new(root) {
  animation-duration: 0.5s;
}
```
