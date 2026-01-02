# 01. 選擇器、權重與級聯 (Selectors, Specificity & Cascade)

## 1. 基礎語法 (Syntax)

```css
selector {
  property: value;
}
```

## 2. 選擇器列表 (Selectors)

### 基本選擇器
| 選擇器 | 範例 | 描述 |
| :--- | :--- | :--- |
| 通用選擇器 | `*` | 選取所有元素。 |
| 元素選擇器 | `div` | 選取所有指定類型的標籤。 |
| ID 選擇器 | `#header` | 選取 `id="header"` 的元素 (頁面中應唯一)。 |
| 類別選擇器 | `.btn` | 選取所有 `class="btn"` 的元素。 |

### 組合選擇器 (Combinators)
| 類型 | 符號 | 範例 | 描述 |
| :--- | :--- | :--- | :--- |
| 後代選擇器 | (空白) | `div p` | 選取 `div` 內部的所有 `p` (包含孫層級)。 |
| 子代選擇器 | `>` | `ul > li` | 僅選取 `ul` 的直接子層 `li`。 |
| 相鄰兄弟 | `+` | `h1 + p` | 選取緊接在 `h1` 後的第一個 `p`。 |
| 通用兄弟 | `~` | `h1 ~ p` | 選取 `h1` 之後的所有同層級 `p`。 |

### 屬性選擇器 (Attribute Selectors)
- `[attr]`: 具有該屬性。
- `[attr=value]`: 屬性值完全符合。
- `[attr^=value]`: 屬性值以...開頭。
- `[attr$=value]`: 屬性值以...結尾。
- `[attr*=value]`: 屬性值包含...。

### 偽類 (Pseudo-classes)
- **狀態類**: `:hover`, `:active`, `:focus`, `:visited`, `:checked`, `:disabled`.
- **結構類**: 
    - `:first-child`, `:last-child`
    - `:nth-child(n)` (如 `2n`, `odd`, `3`)
    - `:not(selector)` (排除法)
    - `:is()`, `:where()`, `:has()` (現代 CSS 邏輯選擇器)

### 偽元素 (Pseudo-elements)
- `::before`: 元素內容之前插入。
- `::after`: 元素內容之後插入。
- `::placeholder`: 表單佔位符文字。
- `::selection`: 被使用者選取的文字。

## 3. 優先權重 (Specificity)

瀏覽器依據權重決定套用哪條規則。權重計算方式通常表示為 `(ID, Class, Element)` 的三位數：

1.  **`!important`**: 最高優先級 (盡量少用)。
2.  **行內樣式 (Inline Style)**: `style="..."` (權重 1000)。
3.  **ID 選擇器**: `#id` (權重 100)。
4.  **類別/偽類/屬性**: `.class`, `:hover`, `[type]` (權重 10)。
5.  **元素/偽元素**: `div`, `::before` (權重 1)。
6.  **通用選擇器**: `*` (權重 0)。

**範例：**
- `#nav .item` = 100 + 10 = 110
- `.card .title` = 10 + 10 = 20

## 4. 級聯與繼承 (Cascade & Inheritance)

- **級聯 (Cascade)**: 當權重相同時，**後寫**的規則會覆蓋先寫的規則。
- **繼承 (Inheritance)**: 某些屬性會從父元素傳給子元素 (如 `color`, `font-family`, `text-align`)；佈局類屬性通常不繼承 (如 `width`, `margin`, `padding`)。
    - 強制繼承: `property: inherit;`
    - 強制重置: `property: initial;`
    - 還原預設: `property: unset;`
