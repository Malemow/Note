# 表格標籤

> 用於建立表格資料呈現的 HTML 標籤

## 📑 目錄

- [\<table\> 表格](#table-表格)
- [\<tr\> 表格列](#tr-表格列)
- [\<td\> 表格儲存格](#td-表格儲存格)
- [\<th\> 表格標題儲存格](#th-表格標題儲存格)
- [\<thead\> 表格標題區](#thead-表格標題區)
- [\<tbody\> 表格主體區](#tbody-表格主體區)
- [\<tfoot\> 表格頁尾區](#tfoot-表格頁尾區)
- [\<caption\> 表格標題](#caption-表格標題)
- [\<col\> 欄位設定](#col-欄位設定)
- [\<colgroup\> 欄位群組](#colgroup-欄位群組)
- [實際應用範例](#實際應用範例)

---

## \<table\> 表格

### 說明
`<table>` 標籤用於建立 HTML 表格，以行和列的方式呈現資料。表格應該用於顯示表格式資料，而非用於頁面布局。

### 語法
```html
<table>
    <!-- 表格內容 -->
</table>
```

### 全域屬性
支援所有 HTML 全域屬性

### 已廢棄屬性
| 屬性 | 說明 | 替代方案 |
|------|------|---------|
| `border` | 邊框寬度 | CSS `border` |
| `cellpadding` | 儲存格內距 | CSS `padding` |
| `cellspacing` | 儲存格間距 | CSS `border-spacing` |
| `width` | 表格寬度 | CSS `width` |
| `bgcolor` | 背景顏色 | CSS `background-color` |
| `align` | 對齊方式 | CSS `float` 或 `margin` |

### 📌 程式碼範例

#### 基本表格
```html
<table>
    <tr>
        <th>姓名</th>
        <th>年齡</th>
        <th>城市</th>
    </tr>
    <tr>
        <td>張小明</td>
        <td>25</td>
        <td>台北</td>
    </tr>
    <tr>
        <td>李小華</td>
        <td>30</td>
        <td>台中</td>
    </tr>
</table>
```

#### 完整結構表格
```html
<table>
    <caption>員工資料表</caption>
    <thead>
        <tr>
            <th>ID</th>
            <th>姓名</th>
            <th>部門</th>
            <th>薪資</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>001</td>
            <td>張小明</td>
            <td>工程部</td>
            <td>50,000</td>
        </tr>
        <tr>
            <td>002</td>
            <td>李小華</td>
            <td>設計部</td>
            <td>45,000</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">總計</td>
            <td>95,000</td>
        </tr>
    </tfoot>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th style="padding: 8px; background-color: #f0f0f0;">科目</th>
        <th style="padding: 8px; background-color: #f0f0f0;">分數</th>
    </tr>
    <tr>
        <td style="padding: 8px;">數學</td>
        <td style="padding: 8px;">95</td>
    </tr>
    <tr>
        <td style="padding: 8px;">英文</td>
        <td style="padding: 8px;">88</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
table {
    display: table;
    border-collapse: separate;
    border-spacing: 2px;
    border-color: gray;
}
```

### CSS 樣式化

#### 基本樣式
```html
<style>
    .styled-table {
        border-collapse: collapse;
        width: 100%;
    }
    .styled-table th,
    .styled-table td {
        border: 1px solid #ddd;
        padding: 12px;
        text-align: left;
    }
    .styled-table th {
        background-color: #0066cc;
        color: white;
    }
    .styled-table tr:nth-child(even) {
        background-color: #f2f2f2;
    }
    .styled-table tr:hover {
        background-color: #ddd;
    }
</style>

<table class="styled-table">
    <tr>
        <th>欄位 1</th>
        <th>欄位 2</th>
    </tr>
    <tr>
        <td>資料 1</td>
        <td>資料 2</td>
    </tr>
</table>
```

### 無障礙建議
- ✅ 使用 `<caption>` 提供表格說明
- ✅ 使用 `<th>` 標記標題儲存格
- ✅ 為 `<th>` 加上 `scope` 屬性
- ✅ 複雜表格使用 `id` 和 `headers` 屬性
- ❌ 不要用表格做版面布局

### 使用注意事項
```html
<!-- ❌ 錯誤：用表格做布局 -->
<table>
    <tr>
        <td>導航</td>
        <td>主要內容</td>
        <td>側邊欄</td>
    </tr>
</table>

<!-- ✅ 正確：用 CSS 布局 -->
<div style="display: grid; grid-template-columns: 1fr 3fr 1fr;">
    <nav>導航</nav>
    <main>主要內容</main>
    <aside>側邊欄</aside>
</div>

<!-- ✅ 正確：表格用於資料 -->
<table>
    <tr>
        <th>產品</th>
        <th>價格</th>
    </tr>
    <tr>
        <td>筆記型電腦</td>
        <td>30,000</td>
    </tr>
</table>
```

---

## \<tr\> 表格列

### 說明
`<tr>` (table row) 標籤定義表格中的一個列（橫排），包含一個或多個儲存格（`<td>` 或 `<th>`）。

### 語法
```html
<table>
    <tr>
        <td>儲存格 1</td>
        <td>儲存格 2</td>
    </tr>
</table>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 基本用法
```html
<table>
    <tr>
        <th>標題 1</th>
        <th>標題 2</th>
    </tr>
    <tr>
        <td>資料 1</td>
        <td>資料 2</td>
    </tr>
    <tr>
        <td>資料 3</td>
        <td>資料 4</td>
    </tr>
</table>
```

#### 混合標題和資料儲存格
```html
<table>
    <tr>
        <th>姓名</th>
        <td>張小明</td>
    </tr>
    <tr>
        <th>年齡</th>
        <td>25</td>
    </tr>
    <tr>
        <th>職業</th>
        <td>工程師</td>
    </tr>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse;">
    <tr>
        <th style="padding: 8px; background-color: #f0f0f0;">項目</th>
        <th style="padding: 8px; background-color: #f0f0f0;">數值</th>
    </tr>
    <tr>
        <td style="padding: 8px;">項目 A</td>
        <td style="padding: 8px;">100</td>
    </tr>
    <tr>
        <td style="padding: 8px;">項目 B</td>
        <td style="padding: 8px;">200</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### CSS 樣式化
```html
<style>
    tr:nth-child(odd) {
        background-color: #f9f9f9;
    }
    tr:nth-child(even) {
        background-color: #ffffff;
    }
    tr:hover {
        background-color: #e0f7ff;
    }
</style>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：tr 內直接放文字 -->
<tr>
    這是錯誤的
</tr>

<!-- ✅ 正確：tr 只包含 td 或 th -->
<tr>
    <td>正確的</td>
</tr>

<!-- ❌ 錯誤：tr 在 table 外 -->
<tr>
    <td>錯誤</td>
</tr>

<!-- ✅ 正確：tr 在 table、thead、tbody 或 tfoot 內 -->
<table>
    <tr>
        <td>正確</td>
    </tr>
</table>
```

---

## \<td\> 表格儲存格

### 說明
`<td>` (table data) 標籤定義表格中的標準資料儲存格，包含表格的實際資料內容。

### 語法
```html
<tr>
    <td>儲存格內容</td>
</tr>
```

### 常用屬性

| 屬性 | 說明 | 值 | 範例 |
|------|------|-----|------|
| `colspan` | 橫跨欄位數 | 數字 | `colspan="2"` |
| `rowspan` | 橫跨列數 | 數字 | `rowspan="3"` |
| `headers` | 關聯標題儲存格 ID | ID 列表 | `headers="h1 h2"` |

### 已廢棄屬性
| 屬性 | 替代方案 |
|------|---------|
| `align`, `valign` | CSS `text-align`, `vertical-align` |
| `width`, `height` | CSS `width`, `height` |
| `bgcolor` | CSS `background-color` |

### 📌 程式碼範例

#### 基本儲存格
```html
<table>
    <tr>
        <td>姓名</td>
        <td>張小明</td>
    </tr>
    <tr>
        <td>年齡</td>
        <td>25</td>
    </tr>
</table>
```

#### 使用 colspan（合併欄位）
```html
<table border="1">
    <tr>
        <td colspan="3">這個儲存格橫跨 3 欄</td>
    </tr>
    <tr>
        <td>欄位 1</td>
        <td>欄位 2</td>
        <td>欄位 3</td>
    </tr>
</table>
```

#### 使用 rowspan（合併列）
```html
<table border="1">
    <tr>
        <td rowspan="2">這個儲存格橫跨 2 列</td>
        <td>資料 1</td>
    </tr>
    <tr>
        <td>資料 2</td>
    </tr>
</table>
```

#### 複雜合併
```html
<table border="1">
    <tr>
        <td rowspan="2">A</td>
        <td colspan="2">B</td>
    </tr>
    <tr>
        <td>C</td>
        <td>D</td>
    </tr>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

基本表格：
<table border="1" style="border-collapse: collapse;">
    <tr>
        <td style="padding: 8px;">儲存格 1</td>
        <td style="padding: 8px;">儲存格 2</td>
    </tr>
    <tr>
        <td style="padding: 8px;">儲存格 3</td>
        <td style="padding: 8px;">儲存格 4</td>
    </tr>
</table>

合併欄位：
<table border="1" style="border-collapse: collapse;">
    <tr>
        <td colspan="2" style="padding: 8px; text-align: center;">合併的儲存格</td>
    </tr>
    <tr>
        <td style="padding: 8px;">儲存格 1</td>
        <td style="padding: 8px;">儲存格 2</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項
```html
<!-- ❌ 錯誤：td 在 tr 外 -->
<td>錯誤</td>

<!-- ✅ 正確：td 在 tr 內 -->
<table>
    <tr>
        <td>正確</td>
    </tr>
</table>

<!-- ❌ 錯誤：colspan 數量超過實際欄位 -->
<table>
    <tr>
        <td colspan="5">太多欄</td>
    </tr>
    <tr>
        <td>欄1</td>
        <td>欄2</td>
    </tr>
</table>

<!-- ✅ 正確：colspan 對應欄位數 -->
<table>
    <tr>
        <td colspan="2">兩欄</td>
    </tr>
    <tr>
        <td>欄1</td>
        <td>欄2</td>
    </tr>
</table>
```

---

## \<th\> 表格標題儲存格

### 說明
`<th>` (table header) 標籤定義表格的標題儲存格，通常會以粗體置中顯示。對於無障礙性非常重要。

### 語法
```html
<tr>
    <th>標題</th>
</tr>
```

### 常用屬性

| 屬性 | 說明 | 值 | 預設 |
|------|------|-----|------|
| `scope` | 標題作用範圍 | `row`, `col`, `rowgroup`, `colgroup` | - |
| `colspan` | 橫跨欄位數 | 數字 | `1` |
| `rowspan` | 橫跨列數 | 數字 | `1` |
| `abbr` | 標題縮寫 | 文字 | - |

### 📌 程式碼範例

#### 欄位標題
```html
<table border="1">
    <tr>
        <th scope="col">姓名</th>
        <th scope="col">年齡</th>
        <th scope="col">城市</th>
    </tr>
    <tr>
        <td>張小明</td>
        <td>25</td>
        <td>台北</td>
    </tr>
</table>
```

#### 列標題
```html
<table border="1">
    <tr>
        <th scope="row">Q1</th>
        <td>100,000</td>
        <td>120,000</td>
    </tr>
    <tr>
        <th scope="row">Q2</th>
        <td>110,000</td>
        <td>130,000</td>
    </tr>
</table>
```

#### 雙向標題
```html
<table border="1">
    <tr>
        <th></th>
        <th scope="col">2024</th>
        <th scope="col">2025</th>
    </tr>
    <tr>
        <th scope="row">銷售額</th>
        <td>100 萬</td>
        <td>120 萬</td>
    </tr>
    <tr>
        <th scope="row">利潤</th>
        <td>20 萬</td>
        <td>30 萬</td>
    </tr>
</table>
```

#### 使用 abbr 屬性
```html
<table>
    <tr>
        <th abbr="名稱">產品名稱</th>
        <th abbr="價格">建議售價（含稅）</th>
    </tr>
    <tr>
        <td>筆記型電腦</td>
        <td>NT$ 30,000</td>
    </tr>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th style="padding: 8px; background-color: #f0f0f0;">科目</th>
        <th style="padding: 8px; background-color: #f0f0f0;">上學期</th>
        <th style="padding: 8px; background-color: #f0f0f0;">下學期</th>
    </tr>
    <tr>
        <th style="padding: 8px; background-color: #f9f9f9;">數學</th>
        <td style="padding: 8px;">90</td>
        <td style="padding: 8px;">95</td>
    </tr>
    <tr>
        <th style="padding: 8px; background-color: #f9f9f9;">英文</th>
        <td style="padding: 8px;">85</td>
        <td style="padding: 8px;">88</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
th {
    display: table-cell;
    vertical-align: inherit;
    font-weight: bold;
    text-align: center;
}
```

### scope 屬性詳解

| 值 | 說明 | 使用時機 |
|---|------|---------|
| `col` | 欄位標題 | 垂直方向的標題 |
| `row` | 列標題 | 水平方向的標題 |
| `colgroup` | 欄位群組標題 | 多欄的群組標題 |
| `rowgroup` | 列群組標題 | 多列的群組標題 |

### 無障礙建議
- ✅ **務必使用 `scope` 屬性**，幫助螢幕閱讀器
- ✅ 簡單表格用 `scope`，複雜表格用 `id` + `headers`
- ✅ 標題文字要清楚描述欄位內容
- ✅ 避免空白標題（至少使用 `<th scope="col"></th>`）

### 使用注意事項
```html
<!-- ❌ 錯誤：標題用 td -->
<tr>
    <td><strong>姓名</strong></td>
    <td><strong>年齡</strong></td>
</tr>

<!-- ✅ 正確：使用 th -->
<tr>
    <th scope="col">姓名</th>
    <th scope="col">年齡</th>
</tr>

<!-- ✅ 正確：為 th 加上 scope -->
<tr>
    <th scope="col">欄位標題</th>
</tr>
<tr>
    <th scope="row">列標題</th>
    <td>資料</td>
</tr>
```

---

## \<thead\> 表格標題區

### 說明
`<thead>` (table head) 標籤定義表格的標題區域，通常包含欄位標題。可以讓瀏覽器在列印時在每頁頂部重複顯示標題。

### 語法
```html
<table>
    <thead>
        <tr>
            <th>標題1</th>
            <th>標題2</th>
        </tr>
    </thead>
</table>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 基本用法
```html
<table>
    <thead>
        <tr>
            <th>產品</th>
            <th>價格</th>
            <th>庫存</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>筆記型電腦</td>
            <td>30,000</td>
            <td>15</td>
        </tr>
        <tr>
            <td>滑鼠</td>
            <td>500</td>
            <td>100</td>
        </tr>
    </tbody>
</table>
```

#### 多列標題
```html
<table>
    <thead>
        <tr>
            <th rowspan="2">產品</th>
            <th colspan="2">2024</th>
            <th colspan="2">2025</th>
        </tr>
        <tr>
            <th>Q1</th>
            <th>Q2</th>
            <th>Q1</th>
            <th>Q2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>產品 A</td>
            <td>100</td>
            <td>120</td>
            <td>130</td>
            <td>140</td>
        </tr>
    </tbody>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <thead style="background-color: #4CAF50; color: white;">
        <tr>
            <th style="padding: 12px;">員工編號</th>
            <th style="padding: 12px;">姓名</th>
            <th style="padding: 12px;">部門</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="padding: 8px;">001</td>
            <td style="padding: 8px;">張小明</td>
            <td style="padding: 8px;">工程部</td>
        </tr>
        <tr>
            <td style="padding: 8px;">002</td>
            <td style="padding: 8px;">李小華</td>
            <td style="padding: 8px;">設計部</td>
        </tr>
    </tbody>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項
```html
<!-- ✅ 正確：thead 在 tbody 前 -->
<table>
    <thead>
        <tr><th>標題</th></tr>
    </thead>
    <tbody>
        <tr><td>資料</td></tr>
    </tbody>
</table>

<!-- ❌ 錯誤：thead 在 tbody 後 -->
<table>
    <tbody>
        <tr><td>資料</td></tr>
    </tbody>
    <thead>
        <tr><th>標題</th></tr>
    </thead>
</table>

<!-- ✅ 正確順序：caption -> colgroup -> thead -> tbody -> tfoot -->
<table>
    <caption>標題</caption>
    <thead>...</thead>
    <tbody>...</tbody>
    <tfoot>...</tfoot>
</table>
```

---

## \<tbody\> 表格主體區

### 說明
`<tbody>` (table body) 標籤定義表格的主體內容區域，包含表格的主要資料列。

### 語法
```html
<table>
    <tbody>
        <tr>
            <td>資料</td>
        </tr>
    </tbody>
</table>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 基本用法
```html
<table>
    <thead>
        <tr>
            <th>姓名</th>
            <th>分數</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>張小明</td>
            <td>85</td>
        </tr>
        <tr>
            <td>李小華</td>
            <td>90</td>
        </tr>
        <tr>
            <td>王小英</td>
            <td>88</td>
        </tr>
    </tbody>
</table>
```

#### 多個 tbody（分組資料）
```html
<table>
    <thead>
        <tr>
            <th>學生</th>
            <th>分數</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th colspan="2">A 班</th>
        </tr>
        <tr>
            <td>張小明</td>
            <td>85</td>
        </tr>
        <tr>
            <td>李小華</td>
            <td>90</td>
        </tr>
    </tbody>
    <tbody>
        <tr>
            <th colspan="2">B 班</th>
        </tr>
        <tr>
            <td>王小英</td>
            <td>88</td>
        </tr>
        <tr>
            <td>陳小傑</td>
            <td>92</td>
        </tr>
    </tbody>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <thead>
        <tr style="background-color: #f0f0f0;">
            <th style="padding: 8px;">項目</th>
            <th style="padding: 8px;">數量</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="padding: 8px;">項目 A</td>
            <td style="padding: 8px;">10</td>
        </tr>
        <tr>
            <td style="padding: 8px;">項目 B</td>
            <td style="padding: 8px;">20</td>
        </tr>
        <tr>
            <td style="padding: 8px;">項目 C</td>
            <td style="padding: 8px;">15</td>
        </tr>
    </tbody>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### CSS 樣式化
```html
<style>
    tbody tr:nth-child(odd) {
        background-color: #f9f9f9;
    }
    tbody tr:hover {
        background-color: #e0f7ff;
    }
</style>
```

### 使用注意事項
- ✅ 可以有多個 `<tbody>`，用於分組資料
- ✅ 如果沒有明確使用 `<tbody>`，瀏覽器會自動加入
- ✅ `<tbody>` 只能包含 `<tr>` 元素

---

## \<tfoot\> 表格頁尾區

### 說明
`<tfoot>` (table foot) 標籤定義表格的頁尾區域，通常包含總計、摘要等資訊。

### 語法
```html
<table>
    <tfoot>
        <tr>
            <td>頁尾內容</td>
        </tr>
    </tfoot>
</table>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 總計列
```html
<table>
    <thead>
        <tr>
            <th>產品</th>
            <th>數量</th>
            <th>單價</th>
            <th>小計</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>產品 A</td>
            <td>5</td>
            <td>100</td>
            <td>500</td>
        </tr>
        <tr>
            <td>產品 B</td>
            <td>3</td>
            <td>200</td>
            <td>600</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th colspan="3">總計</th>
            <td>1,100</td>
        </tr>
    </tfoot>
</table>
```

#### 多列頁尾
```html
<table>
    <thead>
        <tr>
            <th>項目</th>
            <th>金額</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>收入</td>
            <td>100,000</td>
        </tr>
        <tr>
            <td>支出</td>
            <td>60,000</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th>小計</th>
            <td>40,000</td>
        </tr>
        <tr>
            <th>稅金 (5%)</th>
            <td>2,000</td>
        </tr>
        <tr>
            <th>總計</th>
            <td>38,000</td>
        </tr>
    </tfoot>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <thead>
        <tr style="background-color: #f0f0f0;">
            <th style="padding: 8px;">科目</th>
            <th style="padding: 8px;">分數</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="padding: 8px;">數學</td>
            <td style="padding: 8px;">90</td>
        </tr>
        <tr>
            <td style="padding: 8px;">英文</td>
            <td style="padding: 8px;">85</td>
        </tr>
    </tbody>
    <tfoot style="background-color: #e0e0e0; font-weight: bold;">
        <tr>
            <td style="padding: 8px;">平均</td>
            <td style="padding: 8px;">87.5</td>
        </tr>
    </tfoot>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 重要注意事項
- ⚠️ HTML5 中，`<tfoot>` 必須放在 `<tbody>` **之後**
- ⚠️ 但在 HTML4 中，`<tfoot>` 要放在 `<tbody>` **之前**
- ✅ 建議統一放在 `<tbody>` 之後（遵循 HTML5）

```html
<!-- ✅ HTML5 正確順序 -->
<table>
    <thead>...</thead>
    <tbody>...</tbody>
    <tfoot>...</tfoot>
</table>
```

---

## \<caption\> 表格標題

### 說明
`<caption>` 標籤定義表格的標題或說明，必須是 `<table>` 的第一個子元素。對於無障礙性很重要。

### 語法
```html
<table>
    <caption>表格標題</caption>
    <!-- 其他表格內容 -->
</table>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 基本用法
```html
<table>
    <caption>2025 年銷售統計</caption>
    <tr>
        <th>月份</th>
        <th>銷售額</th>
    </tr>
    <tr>
        <td>一月</td>
        <td>100,000</td>
    </tr>
</table>
```

#### 包含格式化文字
```html
<table>
    <caption>
        <strong>員工資料表</strong>
        <br>
        <small>更新日期：2026-01-02</small>
    </caption>
    <thead>
        <tr>
            <th>姓名</th>
            <th>部門</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>張小明</td>
            <td>工程部</td>
        </tr>
    </tbody>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <caption style="caption-side: top; padding: 10px; font-weight: bold; font-size: 1.1em;">
        學生成績表
    </caption>
    <tr>
        <th style="padding: 8px; background-color: #f0f0f0;">姓名</th>
        <th style="padding: 8px; background-color: #f0f0f0;">成績</th>
    </tr>
    <tr>
        <td style="padding: 8px;">張小明</td>
        <td style="padding: 8px;">85</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
caption {
    display: table-caption;
    text-align: center;
}
```

### CSS 樣式化
```html
<style>
    caption {
        caption-side: top; /* top 或 bottom */
        text-align: left;
        font-weight: bold;
        padding: 10px;
        background-color: #f0f0f0;
    }
</style>
```

### 無障礙建議
- ✅ **強烈建議使用** `<caption>` 為表格提供說明
- ✅ 標題要清楚描述表格內容
- ✅ 螢幕閱讀器會優先朗讀 caption
- ✅ 有助於理解複雜表格的用途

### 使用注意事項
```html
<!-- ✅ 正確：caption 是 table 的第一個子元素 -->
<table>
    <caption>標題</caption>
    <thead>...</thead>
</table>

<!-- ❌ 錯誤：caption 不是第一個 -->
<table>
    <thead>...</thead>
    <caption>標題</caption>
</table>

<!-- ❌ 錯誤：多個 caption -->
<table>
    <caption>標題1</caption>
    <caption>標題2</caption>
</table>

<!-- ✅ 正確：每個表格只有一個 caption -->
<table>
    <caption>唯一的標題</caption>
</table>
```

---

## \<col\> 欄位設定

### 說明
`<col>` 標籤用於為表格的一個或多個欄位設定屬性，如寬度、樣式等。這是一個空元素。

### 語法
```html
<table>
    <colgroup>
        <col style="width: 100px;">
        <col style="width: 200px;">
    </colgroup>
</table>
```

### 常用屬性

| 屬性 | 說明 | 值 |
|------|------|-----|
| `span` | 影響的欄位數 | 數字（預設 1） |

### 📌 程式碼範例

#### 設定欄位寬度
```html
<table>
    <colgroup>
        <col style="width: 50px;">
        <col style="width: 200px;">
        <col style="width: 100px;">
    </colgroup>
    <tr>
        <th>編號</th>
        <th>名稱</th>
        <th>價格</th>
    </tr>
    <tr>
        <td>1</td>
        <td>產品名稱</td>
        <td>1000</td>
    </tr>
</table>
```

#### 使用 span
```html
<table>
    <colgroup>
        <col span="2" style="background-color: #f0f0f0;">
        <col style="background-color: #e0e0e0;">
    </colgroup>
    <tr>
        <th>欄位 1</th>
        <th>欄位 2</th>
        <th>欄位 3</th>
    </tr>
</table>
```

#### 欄位樣式
```html
<table>
    <colgroup>
        <col style="background-color: #ffe6e6;">
        <col style="background-color: #e6f3ff;">
        <col style="background-color: #e6ffe6;">
    </colgroup>
    <tr>
        <td>紅色背景欄</td>
        <td>藍色背景欄</td>
        <td>綠色背景欄</td>
    </tr>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <colgroup>
        <col style="background-color: #ffe6e6; width: 30%;">
        <col style="background-color: #e6f3ff; width: 40%;">
        <col style="background-color: #e6ffe6; width: 30%;">
    </colgroup>
    <tr>
        <th style="padding: 8px;">欄位 A</th>
        <th style="padding: 8px;">欄位 B</th>
        <th style="padding: 8px;">欄位 C</th>
    </tr>
    <tr>
        <td style="padding: 8px;">資料 1</td>
        <td style="padding: 8px;">資料 2</td>
        <td style="padding: 8px;">資料 3</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 限制
⚠️ `<col>` 只能設定部分 CSS 屬性：
- ✅ `width`
- ✅ `background`（background-color, background-image 等）
- ✅ `border`
- ✅ `visibility`
- ❌ 其他屬性（如 `text-align`, `font-size` 等）**無效**

---

## \<colgroup\> 欄位群組

### 說明
`<colgroup>` 標籤用於將表格的欄位分組，可以包含多個 `<col>` 元素或自己設定 `span` 屬性。

### 語法
```html
<table>
    <colgroup>
        <col>
        <col>
    </colgroup>
</table>
```

### 常用屬性

| 屬性 | 說明 | 值 |
|------|------|-----|
| `span` | 群組包含的欄位數 | 數字 |

### 📌 程式碼範例

#### 基本用法
```html
<table>
    <colgroup>
        <col style="background-color: #f0f0f0;">
        <col span="2" style="background-color: #e0e0e0;">
    </colgroup>
    <tr>
        <th>欄1</th>
        <th>欄2</th>
        <th>欄3</th>
    </tr>
</table>
```

#### 多個 colgroup
```html
<table>
    <colgroup span="2" style="background-color: #ffe6e6;"></colgroup>
    <colgroup span="2" style="background-color: #e6ffe6;"></colgroup>
    <tr>
        <th>A1</th>
        <th>A2</th>
        <th>B1</th>
        <th>B2</th>
    </tr>
</table>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<table border="1" style="border-collapse: collapse; width: 100%;">
    <colgroup>
        <col style="background-color: #fff3cd;">
    </colgroup>
    <colgroup span="2" style="background-color: #d1ecf1;">
    </colgroup>
    <tr>
        <th style="padding: 8px;">名稱</th>
        <th style="padding: 8px;">2024</th>
        <th style="padding: 8px;">2025</th>
    </tr>
    <tr>
        <td style="padding: 8px;">產品 A</td>
        <td style="padding: 8px;">100</td>
        <td style="padding: 8px;">120</td>
    </tr>
</table>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 使用注意事項
```html
<!-- ✅ 正確：colgroup 在 thead 前 -->
<table>
    <colgroup>
        <col>
    </colgroup>
    <thead>...</thead>
</table>

<!-- ❌ 錯誤：colgroup 在內容後 -->
<table>
    <thead>...</thead>
    <colgroup>
        <col>
    </colgroup>
</table>
```

---

## 實際應用範例

### 產品價格表
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <caption style="font-weight: bold; padding: 10px; background-color: #f5f5f5;">
        產品價格對照表
    </caption>

    <colgroup>
        <col style="width: 40%;">
        <col style="width: 20%; background-color: #ffe6e6;">
        <col style="width: 20%; background-color: #e6ffe6;">
        <col style="width: 20%;">
    </colgroup>

    <thead style="background-color: #0066cc; color: white;">
        <tr>
            <th style="padding: 12px;">產品名稱</th>
            <th style="padding: 12px;">原價</th>
            <th style="padding: 12px;">特價</th>
            <th style="padding: 12px;">庫存</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td style="padding: 10px;">無線滑鼠</td>
            <td style="padding: 10px; text-decoration: line-through;">NT$ 799</td>
            <td style="padding: 10px; font-weight: bold; color: #d32f2f;">NT$ 599</td>
            <td style="padding: 10px; text-align: center;">50</td>
        </tr>
        <tr>
            <td style="padding: 10px;">機械鍵盤</td>
            <td style="padding: 10px; text-decoration: line-through;">NT$ 2,999</td>
            <td style="padding: 10px; font-weight: bold; color: #d32f2f;">NT$ 2,499</td>
            <td style="padding: 10px; text-align: center;">30</td>
        </tr>
        <tr>
            <td style="padding: 10px;">27吋螢幕</td>
            <td style="padding: 10px; text-decoration: line-through;">NT$ 6,990</td>
            <td style="padding: 10px; font-weight: bold; color: #d32f2f;">NT$ 5,990</td>
            <td style="padding: 10px; text-align: center;">15</td>
        </tr>
    </tbody>

    <tfoot style="background-color: #f5f5f5; font-weight: bold;">
        <tr>
            <td style="padding: 10px;" colspan="3">總節省金額</td>
            <td style="padding: 10px; text-align: center; color: #388e3c;">NT$ 1,500</td>
        </tr>
    </tfoot>
</table>
```

### 課程時間表
```html
<table border="1" style="border-collapse: collapse; width: 100%; text-align: center;">
    <caption style="font-size: 1.2em; font-weight: bold; padding: 15px;">
        本週課程表
    </caption>

    <thead style="background-color: #4CAF50; color: white;">
        <tr>
            <th style="padding: 10px;">時間</th>
            <th style="padding: 10px;">星期一</th>
            <th style="padding: 10px;">星期二</th>
            <th style="padding: 10px;">星期三</th>
            <th style="padding: 10px;">星期四</th>
            <th style="padding: 10px;">星期五</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <th style="padding: 10px; background-color: #f0f0f0;">08:00-09:00</th>
            <td style="padding: 10px;">數學</td>
            <td style="padding: 10px;">英文</td>
            <td style="padding: 10px;">歷史</td>
            <td style="padding: 10px;">數學</td>
            <td style="padding: 10px;">體育</td>
        </tr>
        <tr>
            <th style="padding: 10px; background-color: #f0f0f0;">09:00-10:00</th>
            <td style="padding: 10px;">英文</td>
            <td style="padding: 10px;">數學</td>
            <td style="padding: 10px;">物理</td>
            <td style="padding: 10px;">化學</td>
            <td style="padding: 10px;">國文</td>
        </tr>
        <tr>
            <th style="padding: 10px; background-color: #f0f0f0;">10:00-11:00</th>
            <td style="padding: 10px;">生物</td>
            <td style="padding: 10px;">地理</td>
            <td style="padding: 10px;">英文</td>
            <td style="padding: 10px;">數學</td>
            <td style="padding: 10px;">資訊</td>
        </tr>
        <tr style="background-color: #fff3cd;">
            <th style="padding: 10px; background-color: #f0f0f0;">12:00-13:00</th>
            <td colspan="5" style="padding: 10px; font-weight: bold;">午休時間</td>
        </tr>
        <tr>
            <th style="padding: 10px; background-color: #f0f0f0;">13:00-14:00</th>
            <td style="padding: 10px;">美術</td>
            <td style="padding: 10px;">音樂</td>
            <td style="padding: 10px;">體育</td>
            <td style="padding: 10px;">英文</td>
            <td style="padding: 10px;">社團</td>
        </tr>
    </tbody>
</table>
```

### 複雜合併表格
```html
<table border="1" style="border-collapse: collapse; width: 100%; text-align: center;">
    <caption>2025 年度業績報表</caption>

    <thead>
        <tr style="background-color: #2196F3; color: white;">
            <th rowspan="2" style="padding: 10px;">部門</th>
            <th colspan="4" style="padding: 10px;">季度業績（萬元）</th>
            <th rowspan="2" style="padding: 10px;">年度總計</th>
        </tr>
        <tr style="background-color: #64B5F6; color: white;">
            <th style="padding: 8px;">Q1</th>
            <th style="padding: 8px;">Q2</th>
            <th style="padding: 8px;">Q3</th>
            <th style="padding: 8px;">Q4</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <th style="padding: 8px; background-color: #f0f0f0;">業務部</th>
            <td style="padding: 8px;">500</td>
            <td style="padding: 8px;">550</td>
            <td style="padding: 8px;">600</td>
            <td style="padding: 8px;">650</td>
            <td style="padding: 8px; font-weight: bold;">2,300</td>
        </tr>
        <tr>
            <th style="padding: 8px; background-color: #f0f0f0;">行銷部</th>
            <td style="padding: 8px;">300</td>
            <td style="padding: 8px;">320</td>
            <td style="padding: 8px;">350</td>
            <td style="padding: 8px;">380</td>
            <td style="padding: 8px; font-weight: bold;">1,350</td>
        </tr>
        <tr>
            <th style="padding: 8px; background-color: #f0f0f0;">研發部</th>
            <td style="padding: 8px;">200</td>
            <td style="padding: 8px;">250</td>
            <td style="padding: 8px;">280</td>
            <td style="padding: 8px;">300</td>
            <td style="padding: 8px; font-weight: bold;">1,030</td>
        </tr>
    </tbody>

    <tfoot style="background-color: #e3f2fd; font-weight: bold;">
        <tr>
            <td style="padding: 10px;">季度總計</td>
            <td style="padding: 10px;">1,000</td>
            <td style="padding: 10px;">1,120</td>
            <td style="padding: 10px;">1,230</td>
            <td style="padding: 10px;">1,330</td>
            <td style="padding: 10px; background-color: #1976D2; color: white;">4,680</td>
        </tr>
    </tfoot>
</table>
```

---

## 最佳實踐總結

### ✅ 表格設計原則
1. **語意化使用**：表格用於表格式資料，不用於布局
2. **完整結構**：使用 `<thead>`, `<tbody>`, `<tfoot>` 組織表格
3. **無障礙性**：加上 `<caption>` 和 `<th>` 的 `scope` 屬性
4. **樣式分離**：用 CSS 控制樣式，不用廢棄屬性
5. **響應式設計**：考慮行動裝置的顯示

### ❌ 常見錯誤
1. 用表格做頁面布局（應使用 CSS Grid 或 Flexbox）
2. 未使用 `<th>` 標記標題儲存格
3. 缺少 `<caption>` 說明表格用途
4. `colspan` / `rowspan` 計算錯誤
5. 使用已廢棄的屬性（如 `border`, `cellpadding`）

### 無障礙最佳實踐
```html
<table>
    <!-- 1. 加上 caption -->
    <caption>完整的表格說明</caption>

    <!-- 2. 使用 thead, tbody, tfoot -->
    <thead>
        <tr>
            <!-- 3. 標題儲存格使用 th 和 scope -->
            <th scope="col">欄位標題</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <!-- 4. 列標題也要用 th -->
            <th scope="row">列標題</th>
            <td>資料</td>
        </tr>
    </tbody>
</table>
```

### 響應式表格技巧
```html
<style>
    /* 小螢幕時垂直顯示 */
    @media (max-width: 600px) {
        table, thead, tbody, th, td, tr {
            display: block;
        }
        thead tr {
            position: absolute;
            top: -9999px;
            left: -9999px;
        }
        td {
            position: relative;
            padding-left: 50%;
        }
        td:before {
            content: attr(data-label);
            position: absolute;
            left: 6px;
            font-weight: bold;
        }
    }
</style>

<table>
    <thead>
        <tr>
            <th>姓名</th>
            <th>年齡</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td data-label="姓名">張小明</td>
            <td data-label="年齡">25</td>
        </tr>
    </tbody>
</table>
```

---

[⬆️ 回到頂部](#表格標籤) | [📑 回索引頁](index.md)
