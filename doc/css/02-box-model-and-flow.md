# 02. 盒模型與流 (Box Model, Layout & Flow)

## 1. 盒模型 (CSS Box Model)

所有 HTML 元素都可以視為一個盒子。

### 結構 (由外而內)
1.  **Margin (外邊距)**: 盒子外部的空間，背景透明。會發生「外邊距重疊」(Margin Collapse)。
2.  **Border (邊框)**: 包裹在 Padding 和 Content 外的線條。
3.  **Padding (內邊距)**: Content 與 Border 之間的空間，會顯示背景色。
4.  **Content (內容)**: 實際顯示文字或圖片的區域 (Width/Height)。

### box-sizing 屬性
這是控制盒模型大小計算方式的關鍵屬性。

- `content-box` (預設): `width` 只包含內容。
    - 實際寬度 = `width` + `padding` + `border`
- `border-box` (推薦): `width` 包含內容、內邊距和邊框。
    - 實際寬度 = `width` (Padding 和 Border 會向內擠壓內容)

```css
/* 現代 CSS Reset 常見寫法 */
*, *::before, *::after {
  box-sizing: border-box;
}
```

## 2. 顯示模式 (Display)

`display` 屬性決定元素在文檔流中的行為。

- `block`: 區塊元素。獨佔一行，可設寬高 (如 `div`, `p`, `h1`)。
- `inline`: 行內元素。不換行，寬高由內容決定，設 margin-top/bottom 無效 (如 `span`, `a`)。
- `inline-block`: 像行內元素一樣排列，但可以設定寬高。
- `none`: 隱藏元素 (不佔空間)。

## 3. 定位 (Position)

`position` 屬性用於改變元素的定位方式，需搭配 `top`, `right`, `bottom`, `left` 使用。

| 屬性值 | 描述 | 參考基準 |
| :--- | :--- | :--- |
| `static` | 預設值 | 文檔流自然排列 (top/left 無效)。 |
| `relative` | 相對定位 | 相對於**自己原本的位置**偏移。不改變文檔流佔位。 |
| `absolute` | 絕對定位 | 相對於**最近的非 static 父層**定位。脫離文檔流。 |
| `fixed` | 固定定位 | 相對於**瀏覽器視窗 (Viewport)** 定位。捲動時不移動。 |
| `sticky` | 黏性定位 | 根據捲動位置在 `relative` 和 `fixed` 之間切換。 |

### Z-Index
- 控制堆疊順序 (圖層)。
- 只有 `position` 不是 `static` 的元素才有效。
- 數值越大越上層。

## 4. 浮動與清除 (Float & Clear)

雖然現代多用 Flexbox/Grid，但 Float 仍用於文字環繞圖片。

- `float: left / right`: 元素向左/右浮動，脫離部分文檔流。
- `clear: left / right / both`: 禁止元素兩側有浮動元素 (用於解決父層高度塌陷)。
