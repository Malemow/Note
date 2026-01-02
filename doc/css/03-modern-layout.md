# 03. 現代佈局 (Modern Layout: Flexbox & Grid)

W3C 推薦使用 Flexbox 處理一維佈局，Grid 處理二維佈局。

## 1. Flexbox (彈性盒佈局)

適用於：導覽列、置中對齊、單行或單列排列。

### 父容器屬性 (Container)
- **`display: flex;`**
- **`flex-direction`**: 主軸方向。
    - `row` (預設，左到右), `column` (上到下), `row-reverse`, `column-reverse`.
- **`justify-content`**: 主軸對齊 (如橫向排列時的水平對齊)。
    - `flex-start`, `flex-end`, `center`, `space-between` (分散), `space-around`.
- **`align-items`**: 交叉軸對齊 (如橫向排列時的垂直對齊)。
    - `stretch` (預設，拉伸), `flex-start`, `center`, `baseline`.
- **`flex-wrap`**: 是否換行。
    - `nowrap` (預設), `wrap`.

### 子元素屬性 (Item)
- **`flex: 1;`**: 簡寫，讓元素佔滿剩餘空間。
    - 完整寫法: `flex: <grow> <shrink> <basis>`
- **`order`**: 改變視覺排列順序 (預設 0)。
- **`align-self`**: 覆寫父層的 `align-items`。

---

## 2. CSS Grid (網格佈局)

適用於：整體頁面佈局、複雜的二維排版。

### 父容器屬性 (Container)
- **`display: grid;`**
- **`grid-template-columns`**: 定義欄位寬度。
    - 範例: `100px 1fr 2fr` (第一欄 100px，剩餘空間分給後兩欄，比例 1:2)。
    - `repeat(3, 1fr)`: 建立三個等寬欄。
- **`grid-template-rows`**: 定義列高。
- **`gap`**: 網格間距 (如 `1rem`)。
- **`grid-template-areas`**: 透過命名來排版。

### 子元素屬性 (Item)
- **`grid-column`**: 跨越欄位。
    - 範例: `1 / 3` (從第 1 條格線開始，到第 3 條格線結束，即佔 2 欄)。
    - 範例: `span 2` (跨越 2 欄)。
- **`grid-row`**: 跨越列。
- **`grid-area`**: 指定對應 `grid-template-areas` 的名稱。

---

## 3. 居中終極指南 (Centering)

### 使用 Flexbox
```css
.parent {
  display: flex;
  justify-content: center; /* 主軸居中 */
  align-items: center;     /* 交叉軸居中 */
}
```

### 使用 Grid
```css
.parent {
  display: grid;
  place-items: center; /* 同時水平垂直居中 */
}
```

### 使用 Position
```css
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
