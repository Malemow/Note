# 07. 進階技巧與常見陷阱 (Advanced Patterns & Pitfalls)

這份文件收錄了現代 CSS 的進階邏輯控制、無 JS 互動技巧，以及容易踩坑的權重與繼承問題。

## 1. 子元素影響父元素：`:has()` (The Parent Selector)

在 `:has()` 出現之前，CSS 無法根據子元素的狀態來改變父元素的樣式。現在各大瀏覽器已廣泛支援。

### 基礎語法
```css
/* 如果 .card 裡面有 img，則 .card 背景變黑 */
.card:has(img) {
  background-color: #000;
  color: #fff;
}
```

### 實戰範例 1：根據 Checkbox 狀態改變容器樣式
這在做「選取卡片」或「待辦事項」時非常有用。

```css
/* 當內部的 checkbox 被勾選時，改變整個 row 的背景與邊框 */
.todo-item:has(input[type="checkbox"]:checked) {
  background-color: #f0fdf4;
  border-left: 4px solid #4ade80;
  text-decoration: line-through;
  opacity: 0.8;
}
```

### 實戰範例 2：防止 Grid/Flex 佈局因某個子元素缺失而壞掉
```css
/* 如果 .gallery 裡面沒有任何 .photo，就隱藏整個 gallery */
.gallery:not(:has(.photo)) {
  display: none;
}
```

### 實戰範例 3：前一個兄弟元素影響後一個 (反向選取)
雖然 CSS 只有 `+` (向後選)，但配合 `:has` 可以模擬「向前選」。
```css
/* 當滑鼠懸停在 h2 時，讓它「前面」的 h1 變色 */
/* 邏輯：選取 body，當 body 擁有 (被 hover 的 h2) 時，選取該 body 內的 h1 */
body:has(h2:hover) h1 {
  color: blue;
}
```

---

## 2. 兄弟連動技巧 (The Checkbox/Radio Hack)

在不使用 JavaScript 的情況下，利用 HTML 的 `checkbox` 或 `radio` 的 `:checked` 狀態，配合兄弟選擇器 (`+` 或 `~`) 來控制介面開關。

### 核心原理
1.  **Input**: 隱藏起來的 `checkbox`，負責儲存「開/關」狀態。
2.  **Label**: 使用 `for` 屬性綁定 Input，點擊 Label 等同點擊 Input。
3.  **Content**: 位於 Input 之後的兄弟元素，根據 `:checked` 改變顯示。

### 實戰範例：純 CSS 側邊欄開關 (Sidebar Toggle)

**HTML 結構:**
```html
<input type="checkbox" id="menu-toggle" hidden>

<!-- 觸發按鈕 -->
<label for="menu-toggle" class="hamburger">☰ 選單</label>

<!-- 側邊欄內容 (必須在 input 之後) -->
<nav class="sidebar">
  <ul>...</ul>
</nav>

<!-- 遮罩層 (點擊可關閉) -->
<label for="menu-toggle" class="overlay"></label>
```

**CSS 邏輯:**
```css
/* 1. 初始狀態：側邊欄移出畫面 */
.sidebar {
  position: fixed;
  left: -250px; /* 隱藏在左側 */
  width: 250px;
  height: 100%;
  background: #333;
  transition: left 0.3s ease;
}

.overlay {
  display: none; /* 初始隱藏 */
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.5);
}

/* 2. 當 Checkbox 被勾選時 (~ 選取後面的兄弟) */
#menu-toggle:checked ~ .sidebar {
  left: 0; /* 滑入畫面 */
}

#menu-toggle:checked ~ .overlay {
  display: block; /* 顯示遮罩 */
}
```

---

## 3. 專家級 CSS 邏輯範例 (Expert CSS Patterns)

這區塊展示如何利用 CSS 原生邏輯解決以往需要 JavaScript 的問題。

### 範例 A: 浮動標籤 (Floating Label)
**需求**: Label 預設在輸入框內，當使用者「開始輸入」或「Focus」時，Label 浮動到左上角。
**核心**: 利用 `input:not(:placeholder-shown)` 來偵測是否有內容。

**HTML**:
```html
<div class="input-group">
  <!-- 必須：input 在 label 之前，且 placeholder 不能為空 (給個空白符) -->
  <input type="text" id="username" placeholder=" " required>
  <label for="username">使用者名稱</label>
</div>
```

**CSS**:
```css
.input-group {
  position: relative;
  padding-top: 10px;
}

.input-group input {
  padding: 10px;
  width: 100%;
}

.input-group label {
  position: absolute;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  transition: all 0.2s ease;
  pointer-events: none; /* 讓點擊穿透到 input */
  color: #999;
}

/* 當 input 處於 focus 狀態 或 有內容時 (非 placeholder 顯示狀態) */
.input-group input:focus + label,
.input-group input:not(:placeholder-shown) + label {
  top: 0;
  left: 0;
  transform: translateY(0);
  font-size: 0.8rem;
  color: #333;
}
```

### 範例 B: RAM 佈局 (Responsive Grid without Media Queries)
**需求**: 卡片自動換行，無需寫多個 `@media` 斷點。
**核心**: `Repeat`, `Auto-fit`, `Minmax`.

```css
.grid-container {
  display: grid;
  gap: 1rem;
  
  /* 瀏覽器自動計算：每個欄位最少 250px，若有剩餘空間則平分 (1fr) */
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

### 範例 C: 友善表單驗證 (User-Friendly Validation)
**需求**: 不要一進頁面就顯示紅色錯誤，只有當使用者「輸入過」且「格式錯誤」時才顯示。
**核心**: 排除掉 `:placeholder-shown` (還沒打字) 的狀態。

```css
/* 邏輯：(有打字) AND (格式無效) */
input:not(:placeholder-shown):invalid {
  border-color: red;
  background-color: #ffe6e6;
}

/* 邏輯：(有打字) AND (格式正確) */
input:not(:placeholder-shown):valid {
  border-color: green;
}
```

### 範例 D: 滾動驅動動畫 (Scroll-Driven Animations)
**需求**: 頁面頂部的閱讀進度條，隨捲軸移動。
**核心**: `animation-timeline: scroll()` (目前 Chrome/Edge 支援)。

```css
.progress-bar {
  position: fixed;
  top: 0; left: 0;
  height: 5px;
  background: red;
  width: 100%;
  transform-origin: left;
  
  /* 動畫從 scaleX(0) 到 scaleX(1) */
  animation: grow-progress auto linear;
  animation-timeline: scroll(); 
}

@keyframes grow-progress {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
```

---

## 4. 權重與繼承的陷阱 (Specificity & Inheritance Traps)

### 陷阱 1：`!important` 的濫用循環
- **問題**: 用了 `!important` 覆蓋樣式，結果下次要修改時，被迫用另一個 `!important`。
- **解法**: 盡量提升選擇器權重 (例如多加一層 class 或 ID)，而非使用 `!important`。僅在覆蓋第三方 Library 且無法修改 HTML 時使用。

### 陷阱 2：連結 `<a>` 的顏色繼承
- **問題**: 設定了 `div { color: red; }`，但裡面的 `a` 標籤還是藍色的。
- **原因**: 瀏覽器預設樣式表 (User Agent Stylesheet) 給 `a` 設定了顏色，這屬於「元素選擇器」，優先級高於父層繼承來的顏色。
- **解法**: 強制繼承。
  ```css
  a {
    color: inherit;
    text-decoration: none;
  }
  ```

### 陷阱 3：通用選擇器 `*` 的權重是 0
- **問題**:
  ```css
  * { color: black; }
  .box { color: red; }
  /* .box 內的文字是 red，這沒問題 */
  ```
  但是：
  ```css
  .box { color: red; }
  * { color: black; } 
  /* 如果 * 寫在後面，且 .box 內的元素是 p，p 會變成 black 嗎？ */
  /* 答案：會。因為 p 被 * 選中 (權重0)，而繼承來的 red (沒有權重) 會被覆蓋。 */
  ```
- **觀念**: **直接選中 (即使是 `*`) > 繼承 (Inherited)**。

### 陷阱 4：Flex/Grid Item 的 `min-width` 預設值
- **問題**: 在 Flex 容器內的文字過長，導致容器被撐爆，設了 `width: 100%` 也無效。
- **原因**: Flex 和 Grid 的子元素，其 `min-width` 預設值是 `auto` (內容寬度)，而不是 `0`。
- **解法**:
  ```css
  .flex-item {
    min-width: 0; /* 允許縮小到比內容還小，強迫換行或省略 */
  }
  ```

### 陷阱 5：`100vh` 在手機瀏覽器上的溢出
- **問題**: 設定 `height: 100vh` 在手機 Chrome/Safari 上，會被網址列遮擋底部內容。
- **解法**: 使用新的動態視口單位。
  ```css
  height: 100dvh; /* Dynamic Viewport Height (自動扣除網址列) */
  ```