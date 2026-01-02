# 04. 排版與裝飾 (Typography & Decoration)

## 1. 字體與文字 (Typography)

### 字體屬性
- **`font-family`**: 字體系列。
    - 應提供備選字體: `font-family: "Helvetica Neue", Arial, sans-serif;`
- **`font-size`**: 字體大小。
    - 單位: `px` (絕對), `rem` (相對於根元素), `em` (相對於父元素).
- **`font-weight`**: 粗細。
    - `400` (normal), `700` (bold).
- **`font-style`**: 樣式 (如 `italic`).
- **`line-height`**: 行高。建議使用無單位數值 (如 `1.5`) 以繼承比例。

### 文本屬性
- **`text-align`**: 對齊方式 (`left`, `center`, `right`, `justify`).
- **`text-decoration`**: 裝飾線 (`none`, `underline`, `line-through`).
- **`text-transform`**: 大小寫轉換 (`uppercase`, `lowercase`, `capitalize`).
- **`letter-spacing`**: 字距。
- **`word-spacing`**: 詞距。
- **`white-space`**: 空白處理 (`nowrap` 不換行, `pre` 保留格式).
- **`overflow-wrap` / `word-break`**: 斷行規則。

---

## 2. 顏色與背景 (Colors & Backgrounds)

### 顏色格式
- **關鍵字**: `red`, `blue`, `transparent`.
- **Hex**: `#FF0000` (紅), `#00000080` (半透明黑).
- **RGB/RGBA**: `rgb(255, 0, 0)`, `rgba(0, 0, 0, 0.5)`.
- **HSL/HSLA**: `hsl(0, 100%, 50%)` (色相, 飽和度, 亮度).
- **現代格式**: `lch()`, `lab()` (更廣色域).

### 背景屬性
- **`background-color`**: 背景色。
- **`background-image`**: 背景圖 (`url(...)`) 或 漸層 (`linear-gradient(...)`).
- **`background-size`**: 尺寸。
    - `cover` (填滿，可能裁切), `contain` (完整顯示，可能有留白).
- **`background-position`**: 位置 (如 `center center`).
- **`background-repeat`**: 重複 (`no-repeat`, `repeat-x`).

---

## 3. 邊框與外觀 (Borders & Appearance)

- **`border`**: 簡寫 `1px solid black`.
    - 樣式: `solid`, `dashed` (虛線), `dotted` (點線), `double`.
- **`border-radius`**: 圓角。
    - `50%` 可製作圓形。
- **`box-shadow`**: 陰影。
    - 語法: `offset-x offset-y blur spread color`.
    - 範例: `box-shadow: 0 4px 6px rgba(0,0,0,0.1);`
- **`outline`**: 輪廓線 (不佔空間，常用於 focus 狀態).
- **`opacity`**: 透明度 (0~1，會影響內容).

## 4. 漸層 (Gradients)

漸層被視為 `background-image`。

- **線性漸層**: `linear-gradient(to right, red, blue)`
- **徑向漸層**: `radial-gradient(circle, red, blue)`
