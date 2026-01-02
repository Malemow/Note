# 列表標籤

> 用於建立各種列表結構的 HTML 標籤

## 📑 目錄

- [\<ul\> 無序列表](#ul-無序列表)
- [\<ol\> 有序列表](#ol-有序列表)
- [\<li\> 列表項目](#li-列表項目)
- [\<dl\> 描述列表](#dl-描述列表)
- [\<dt\> 描述術語](#dt-描述術語)
- [\<dd\> 描述定義](#dd-描述定義)
- [實際應用範例](#實際應用範例)

---

## \<ul\> 無序列表

### 說明
`<ul>` (unordered list) 標籤用於建立無序列表，列表項目前面通常會顯示項目符號（bullet points）。適用於項目順序不重要的情況。

### 語法
```html
<ul>
    <li>項目 1</li>
    <li>項目 2</li>
    <li>項目 3</li>
</ul>
```

### 全域屬性
支援所有 HTML 全域屬性

### 已廢棄屬性
| 屬性 | 說明 | 替代方案 |
|------|------|---------|
| `type` | 項目符號樣式 | CSS `list-style-type` |
| `compact` | 緊湊顯示 | CSS `line-height` |

### 📌 程式碼範例

#### 基本無序列表
```html
<ul>
    <li>蘋果</li>
    <li>香蕉</li>
    <li>橘子</li>
</ul>
```

#### 巢狀列表
```html
<ul>
    <li>水果
        <ul>
            <li>蘋果</li>
            <li>香蕉</li>
        </ul>
    </li>
    <li>蔬菜
        <ul>
            <li>紅蘿蔔</li>
            <li>高麗菜</li>
        </ul>
    </li>
</ul>
```

#### 導航選單
```html
<nav>
    <ul>
        <li><a href="/">首頁</a></li>
        <li><a href="/about">關於我們</a></li>
        <li><a href="/products">產品
            <ul>
                <li><a href="/products/software">軟體</a></li>
                <li><a href="/products/hardware">硬體</a></li>
            </ul>
        </a></li>
        <li><a href="/contact">聯絡我們</a></li>
    </ul>
</nav>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<ul>
    <li>第一個項目</li>
    <li>第二個項目</li>
    <li>第三個項目</li>
</ul>

巢狀列表：
<ul>
    <li>主項目 1
        <ul>
            <li>子項目 1.1</li>
            <li>子項目 1.2</li>
        </ul>
    </li>
    <li>主項目 2</li>
</ul>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
ul {
    display: block;
    list-style-type: disc;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0;
    margin-inline-end: 0;
    padding-inline-start: 40px;
}
```

### CSS 樣式化

#### 項目符號樣式
```html
<!-- 實心圓點（預設） -->
<ul style="list-style-type: disc;">
    <li>項目</li>
</ul>

<!-- 空心圓點 -->
<ul style="list-style-type: circle;">
    <li>項目</li>
</ul>

<!-- 實心方塊 -->
<ul style="list-style-type: square;">
    <li>項目</li>
</ul>

<!-- 無符號 -->
<ul style="list-style-type: none;">
    <li>項目</li>
</ul>
```

#### 自訂符號
```html
<style>
    .custom-list {
        list-style: none;
        padding-left: 0;
    }
    .custom-list li::before {
        content: "▶ ";
        color: #0066cc;
    }
</style>

<ul class="custom-list">
    <li>自訂符號項目 1</li>
    <li>自訂符號項目 2</li>
</ul>
```

### 無障礙建議
- ✅ 螢幕閱讀器會宣告列表及項目數量
- ✅ 用於語意化的列表內容，不僅是視覺效果
- ✅ 導航選單建議使用 `<nav>` 包裹
- ❌ 不要只為了縮排而使用列表

### 使用注意事項
```html
<!-- ❌ 錯誤：直接包含文字 -->
<ul>
    這是錯誤的
    <li>項目</li>
</ul>

<!-- ✅ 正確：只包含 li -->
<ul>
    <li>項目 1</li>
    <li>項目 2</li>
</ul>

<!-- ❌ 錯誤：使用廢棄屬性 -->
<ul type="square">
    <li>項目</li>
</ul>

<!-- ✅ 正確：使用 CSS -->
<ul style="list-style-type: square;">
    <li>項目</li>
</ul>
```

---

## \<ol\> 有序列表

### 說明
`<ol>` (ordered list) 標籤用於建立有序列表，列表項目會自動編號。適用於項目順序很重要的情況，如步驟說明、排名等。

### 語法
```html
<ol>
    <li>第一個項目</li>
    <li>第二個項目</li>
    <li>第三個項目</li>
</ol>
```

### 常用屬性

| 屬性 | 說明 | 值 | 預設 |
|------|------|-----|------|
| `type` | 編號類型 | `1` (數字), `A` (大寫字母), `a` (小寫字母), `I` (大寫羅馬), `i` (小寫羅馬) | `1` |
| `start` | 起始編號 | 數字 | `1` |
| `reversed` | 反向編號 | 布林值 | `false` |

### 📌 程式碼範例

#### 基本有序列表
```html
<ol>
    <li>準備材料</li>
    <li>混合材料</li>
    <li>烘烤 30 分鐘</li>
    <li>放涼後享用</li>
</ol>
```

#### 不同編號類型
```html
<!-- 數字（預設） -->
<ol type="1">
    <li>項目一</li>
    <li>項目二</li>
</ol>

<!-- 大寫字母 -->
<ol type="A">
    <li>選項 A</li>
    <li>選項 B</li>
</ol>

<!-- 小寫字母 -->
<ol type="a">
    <li>選項 a</li>
    <li>選項 b</li>
</ol>

<!-- 大寫羅馬數字 -->
<ol type="I">
    <li>第一章</li>
    <li>第二章</li>
</ol>

<!-- 小寫羅馬數字 -->
<ol type="i">
    <li>前言</li>
    <li>正文</li>
</ol>
```

#### 自訂起始編號
```html
<ol start="5">
    <li>第五項</li>
    <li>第六項</li>
    <li>第七項</li>
</ol>
```

#### 反向編號
```html
<ol reversed>
    <li>第三名</li>
    <li>第二名</li>
    <li>第一名</li>
</ol>
```

#### 巢狀有序列表
```html
<ol>
    <li>第一章
        <ol>
            <li>第一節</li>
            <li>第二節</li>
        </ol>
    </li>
    <li>第二章
        <ol>
            <li>第一節</li>
            <li>第二節</li>
        </ol>
    </li>
</ol>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

基本有序列表：
<ol>
    <li>第一步驟</li>
    <li>第二步驟</li>
    <li>第三步驟</li>
</ol>

字母編號：
<ol type="A">
    <li>選項 A</li>
    <li>選項 B</li>
    <li>選項 C</li>
</ol>

從 5 開始編號：
<ol start="5">
    <li>第五項</li>
    <li>第六項</li>
    <li>第七項</li>
</ol>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

**reversed 屬性支援：**
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 18+ | ✅ 18+ | ✅ 6+ | ✅ 79+ | ❌ |

### 預設樣式
```css
ol {
    display: block;
    list-style-type: decimal;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0;
    margin-inline-end: 0;
    padding-inline-start: 40px;
}
```

### CSS 樣式化

#### 自訂編號樣式
```html
<style>
    .custom-counter {
        counter-reset: item;
        list-style: none;
        padding-left: 0;
    }
    .custom-counter li {
        counter-increment: item;
        margin-bottom: 10px;
    }
    .custom-counter li::before {
        content: "步驟 " counter(item) ": ";
        font-weight: bold;
        color: #0066cc;
    }
</style>

<ol class="custom-counter">
    <li>準備材料</li>
    <li>開始製作</li>
    <li>完成</li>
</ol>
```

### 使用場景
✅ **適合使用 `<ol>`：**
- 操作步驟、教學指南
- 排名、名次
- 時間順序的事件
- 法律條文、規章編號
- 目錄章節

❌ **不適合使用 `<ol>`：**
- 無順序關係的項目（用 `<ul>`）
- 僅為視覺編號（用 CSS）

### 使用注意事項
```html
<!-- ✅ 正確：步驟說明 -->
<h3>安裝步驟</h3>
<ol>
    <li>下載安裝檔</li>
    <li>執行安裝程式</li>
    <li>重新啟動電腦</li>
</ol>

<!-- ✅ 正確：混合 ol 和 ul -->
<ol>
    <li>第一步
        <ul>
            <li>注意事項 A</li>
            <li>注意事項 B</li>
        </ul>
    </li>
    <li>第二步</li>
</ol>

<!-- ❌ 錯誤：手動編號 -->
<ul>
    <li>1. 第一項</li>
    <li>2. 第二項</li>
</ul>

<!-- ✅ 正確：使用 ol -->
<ol>
    <li>第一項</li>
    <li>第二項</li>
</ol>
```

---

## \<li\> 列表項目

### 說明
`<li>` (list item) 標籤定義列表中的項目，必須包含在 `<ul>`, `<ol>` 或 `<menu>` 內。

### 語法
```html
<ul>
    <li>項目內容</li>
</ul>
```

### 常用屬性

| 屬性 | 說明 | 適用於 | 值 |
|------|------|--------|-----|
| `value` | 指定項目編號 | `<ol>` 內 | 數字 |

### 📌 程式碼範例

#### 基本使用
```html
<ul>
    <li>簡單文字項目</li>
    <li>包含<strong>格式</strong>的項目</li>
    <li>
        包含多個元素的項目
        <p>這裡有段落</p>
    </li>
</ul>
```

#### 自訂項目編號（僅 ol）
```html
<ol>
    <li>第一項（編號 1）</li>
    <li>第二項（編號 2）</li>
    <li value="10">跳到編號 10</li>
    <li>繼續編號 11</li>
</ol>
```

#### 複雜內容
```html
<ul>
    <li>
        <h4>項目標題</h4>
        <p>項目描述文字...</p>
        <img src="image.jpg" alt="圖片">
    </li>
    <li>
        <h4>另一個項目</h4>
        <p>更多內容...</p>
    </li>
</ul>
```

#### 互動式項目
```html
<ul>
    <li>
        <input type="checkbox" id="task1">
        <label for="task1">完成作業</label>
    </li>
    <li>
        <input type="checkbox" id="task2">
        <label for="task2">回覆郵件</label>
    </li>
</ul>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<ul>
    <li>簡單項目</li>
    <li>包含 <strong>粗體</strong> 和 <em>斜體</em> 的項目</li>
    <li>
        包含多行的項目<br>
        第二行內容
    </li>
</ul>

自訂編號：
<ol>
    <li>項目 1</li>
    <li>項目 2</li>
    <li value="10">項目 10</li>
    <li>項目 11</li>
</ol>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
li {
    display: list-item;
    text-align: match-parent;
}
```

### CSS 樣式化
```html
<style>
    .styled-list li {
        padding: 10px;
        margin-bottom: 5px;
        background-color: #f0f0f0;
        border-left: 4px solid #0066cc;
    }

    .styled-list li:hover {
        background-color: #e0e0e0;
    }
</style>

<ul class="styled-list">
    <li>樣式化項目 1</li>
    <li>樣式化項目 2</li>
    <li>樣式化項目 3</li>
</ul>
```

### 使用注意事項
```html
<!-- ❌ 錯誤：li 在列表外 -->
<li>孤立的項目</li>

<!-- ✅ 正確：li 在列表內 -->
<ul>
    <li>正確的項目</li>
</ul>

<!-- ❌ 錯誤：ul/ol 直接包含非 li 元素 -->
<ul>
    <p>這是錯誤的</p>
    <li>項目</li>
</ul>

<!-- ✅ 正確：非 li 元素放在 li 內 -->
<ul>
    <li>
        <p>這是正確的</p>
    </li>
</ul>
```

---

## \<dl\> 描述列表

### 說明
`<dl>` (description list) 標籤用於建立描述列表，由術語（term）和描述（description）組成，適用於詞彙表、元數據、FAQ 等。

### 語法
```html
<dl>
    <dt>術語</dt>
    <dd>描述</dd>
</dl>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 詞彙表
```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language，超文本標記語言</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets，層疊樣式表</dd>

    <dt>JavaScript</dt>
    <dd>一種高階程式語言，主要用於網頁互動</dd>
</dl>
```

#### 一個術語多個描述
```html
<dl>
    <dt>咖啡</dt>
    <dd>一種由烘焙咖啡豆製成的飲料</dd>
    <dd>含有咖啡因，能提神醒腦</dd>
    <dd>起源於非洲衣索比亞</dd>
</dl>
```

#### 多個術語共享描述
```html
<dl>
    <dt>Firefox</dt>
    <dt>Chrome</dt>
    <dt>Safari</dt>
    <dd>常見的網頁瀏覽器</dd>
</dl>
```

#### 產品資訊
```html
<dl>
    <dt>產品名稱</dt>
    <dd>無線滑鼠</dd>

    <dt>型號</dt>
    <dd>WM-2000</dd>

    <dt>價格</dt>
    <dd>NT$ 599</dd>

    <dt>顏色</dt>
    <dd>黑色</dd>
    <dd>白色</dd>
    <dd>銀色</dd>

    <dt>保固期限</dt>
    <dd>一年</dd>
</dl>
```

#### FAQ 範例
```html
<dl>
    <dt>如何註冊帳號？</dt>
    <dd>
        <p>請點擊右上角的「註冊」按鈕，填寫以下資訊：</p>
        <ul>
            <li>電子郵件地址</li>
            <li>密碼</li>
            <li>使用者名稱</li>
        </ul>
    </dd>

    <dt>忘記密碼怎麼辦？</dt>
    <dd>
        在登入頁面點擊「忘記密碼」連結，
        系統會發送重設密碼的郵件到您的註冊信箱。
    </dd>
</dl>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<dl>
    <dt>HTML</dt>
    <dd>超文本標記語言</dd>

    <dt>CSS</dt>
    <dd>層疊樣式表</dd>

    <dt>JavaScript</dt>
    <dd>網頁程式語言</dd>
</dl>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
dl {
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0;
    margin-inline-end: 0;
}
```

### CSS 樣式化

#### 水平排列
```html
<style>
    .horizontal-dl {
        display: grid;
        grid-template-columns: max-content auto;
        gap: 10px;
    }
    .horizontal-dl dt {
        font-weight: bold;
        grid-column: 1;
    }
    .horizontal-dl dd {
        grid-column: 2;
        margin: 0;
    }
</style>

<dl class="horizontal-dl">
    <dt>姓名：</dt>
    <dd>張小明</dd>

    <dt>年齡：</dt>
    <dd>25 歲</dd>

    <dt>職業：</dt>
    <dd>軟體工程師</dd>
</dl>
```

#### 卡片樣式
```html
<style>
    .card-dl {
        border: 1px solid #ddd;
        border-radius: 8px;
        padding: 20px;
    }
    .card-dl dt {
        font-weight: bold;
        color: #0066cc;
        margin-top: 15px;
    }
    .card-dl dt:first-child {
        margin-top: 0;
    }
    .card-dl dd {
        margin: 5px 0 0 20px;
        color: #666;
    }
</style>

<dl class="card-dl">
    <dt>標題</dt>
    <dd>內容描述...</dd>

    <dt>另一個標題</dt>
    <dd>更多內容...</dd>
</dl>
```

### 使用場景
✅ **適合使用 `<dl>`：**
- 詞彙表、術語定義
- 產品規格、技術規格
- FAQ（常見問題）
- 元數據（metadata）
- 鍵值對資料

❌ **不適合使用 `<dl>`：**
- 對話內容（考慮使用 `<dialog>` 或語意化標籤）
- 一般列表（使用 `<ul>` 或 `<ol>`）

### 使用注意事項
```html
<!-- ❌ 錯誤：dl 直接包含其他元素 -->
<dl>
    <p>這是錯誤的</p>
    <dt>術語</dt>
    <dd>描述</dd>
</dl>

<!-- ✅ 正確：只包含 dt 和 dd -->
<dl>
    <dt>術語</dt>
    <dd>描述</dd>
</dl>

<!-- ❌ 錯誤：dt/dd 在 dl 外 -->
<dt>術語</dt>
<dd>描述</dd>

<!-- ✅ 正確：包在 dl 內 -->
<dl>
    <dt>術語</dt>
    <dd>描述</dd>
</dl>

<!-- ✅ 正確：dd 可包含複雜內容 -->
<dl>
    <dt>問題</dt>
    <dd>
        <p>回答的第一段</p>
        <p>回答的第二段</p>
        <ul>
            <li>要點 1</li>
            <li>要點 2</li>
        </ul>
    </dd>
</dl>
```

---

## \<dt\> 描述術語

### 說明
`<dt>` (description term) 標籤定義描述列表中的術語或名稱，必須在 `<dl>` 內使用。

### 語法
```html
<dl>
    <dt>術語名稱</dt>
    <dd>術語描述</dd>
</dl>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 基本使用
```html
<dl>
    <dt>CPU</dt>
    <dd>Central Processing Unit，中央處理器</dd>
</dl>
```

#### 包含格式化文字
```html
<dl>
    <dt><strong>重要術語</strong></dt>
    <dd>這是重要的定義</dd>

    <dt><code>console.log()</code></dt>
    <dd>JavaScript 中用於輸出訊息的方法</dd>
</dl>
```

#### 連結術語
```html
<dl>
    <dt><a href="#html">HTML</a></dt>
    <dd id="html">超文本標記語言</dd>

    <dt><a href="#css">CSS</a></dt>
    <dd id="css">層疊樣式表</dd>
</dl>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<dl>
    <dt>前端</dt>
    <dd>網頁的視覺和互動部分</dd>

    <dt>後端</dt>
    <dd>伺服器端的邏輯處理</dd>
</dl>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
dt {
    display: block;
}
```

### 使用注意事項
```html
<!-- ✅ 正確：dt 後接 dd -->
<dl>
    <dt>術語</dt>
    <dd>描述</dd>
</dl>

<!-- ✅ 正確：多個 dt 共享一個 dd -->
<dl>
    <dt>術語 1</dt>
    <dt>術語 2</dt>
    <dd>共同的描述</dd>
</dl>

<!-- ✅ 正確：一個 dt 對應多個 dd -->
<dl>
    <dt>術語</dt>
    <dd>描述 1</dd>
    <dd>描述 2</dd>
</dl>
```

---

## \<dd\> 描述定義

### 說明
`<dd>` (description definition) 標籤定義描述列表中術語的描述或定義，必須在 `<dl>` 內使用，並跟隨在 `<dt>` 之後。

### 語法
```html
<dl>
    <dt>術語</dt>
    <dd>術語的描述或定義</dd>
</dl>
```

### 全域屬性
支援所有 HTML 全域屬性

### 📌 程式碼範例

#### 簡單描述
```html
<dl>
    <dt>HTTP</dt>
    <dd>超文本傳輸協定</dd>
</dl>
```

#### 複雜描述
```html
<dl>
    <dt>什麼是響應式設計？</dt>
    <dd>
        <p>響應式網頁設計（Responsive Web Design, RWD）是一種網頁設計方法，
        讓網頁能夠根據不同裝置的螢幕大小自動調整版面配置。</p>

        <p>主要技術包括：</p>
        <ul>
            <li>彈性網格系統</li>
            <li>彈性圖片</li>
            <li>CSS 媒體查詢</li>
        </ul>
    </dd>
</dl>
```

#### 多個描述
```html
<dl>
    <dt>Python</dt>
    <dd>一種高階程式語言</dd>
    <dd>語法簡潔易讀</dd>
    <dd>廣泛應用於資料科學、網頁開發等領域</dd>
</dl>
```

### ✨ 示範效果
> 以下為實際 HTML 渲染效果：

<dl>
    <dt>API</dt>
    <dd>Application Programming Interface（應用程式介面），讓不同程式之間可以互相溝通的介面規範。</dd>
</dl>

### 瀏覽器支援
| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 預設樣式
```css
dd {
    display: block;
    margin-inline-start: 40px;
}
```

### 使用注意事項
```html
<!-- ✅ 正確：dd 跟隨在 dt 後 -->
<dl>
    <dt>術語</dt>
    <dd>描述</dd>
</dl>

<!-- ❌ 錯誤：dd 在 dt 前 -->
<dl>
    <dd>描述</dd>
    <dt>術語</dt>
</dl>

<!-- ✅ 正確：dd 可包含任何內容 -->
<dl>
    <dt>複雜術語</dt>
    <dd>
        <h4>子標題</h4>
        <p>段落文字</p>
        <pre><code>程式碼</code></pre>
    </dd>
</dl>
```

---

## 實際應用範例

### 導航選單
```html
<nav aria-label="主選單">
    <ul>
        <li><a href="/">首頁</a></li>
        <li><a href="/about">關於我們</a></li>
        <li>
            <a href="/products">產品</a>
            <ul>
                <li><a href="/products/web">網頁設計</a></li>
                <li><a href="/products/app">APP 開發</a></li>
                <li><a href="/products/seo">SEO 優化</a></li>
            </ul>
        </li>
        <li><a href="/blog">部落格</a></li>
        <li><a href="/contact">聯絡我們</a></li>
    </ul>
</nav>
```

### 操作步驟
```html
<article>
    <h2>如何製作咖啡</h2>

    <h3>所需材料</h3>
    <ul>
        <li>咖啡豆 20 克</li>
        <li>熱水 200 毫升</li>
        <li>濾紙 1 張</li>
    </ul>

    <h3>製作步驟</h3>
    <ol>
        <li>將咖啡豆磨成中等粗細</li>
        <li>將濾紙放入濾杯，用熱水濕潤</li>
        <li>倒入咖啡粉，輕輕搖平</li>
        <li>倒入少量熱水，悶蒸 30 秒</li>
        <li>以畫圓方式緩慢注水</li>
        <li>等待咖啡完全濾下，即可享用</li>
    </ol>
</article>
```

### 產品規格表
```html
<article>
    <h2>筆記型電腦規格</h2>

    <dl>
        <dt>品牌</dt>
        <dd>TechBrand Pro</dd>

        <dt>型號</dt>
        <dd>TB-2026-X</dd>

        <dt>處理器</dt>
        <dd>Intel Core i7-13700H（第13代）</dd>
        <dd>14核心20線程</dd>
        <dd>基礎頻率：2.4 GHz</dd>
        <dd>最高頻率：5.0 GHz</dd>

        <dt>記憶體</dt>
        <dd>32 GB DDR5</dd>

        <dt>儲存空間</dt>
        <dd>1 TB NVMe SSD</dd>

        <dt>顯示卡</dt>
        <dd>NVIDIA GeForce RTX 4060</dd>
        <dd>8 GB GDDR6</dd>

        <dt>螢幕</dt>
        <dd>15.6 吋 IPS</dd>
        <dd>解析度：2560 x 1440</dd>
        <dd>更新率：165 Hz</dd>

        <dt>重量</dt>
        <dd>2.1 公斤</dd>

        <dt>作業系統</dt>
        <dd>Windows 11 Pro</dd>

        <dt>價格</dt>
        <dd>NT$ 45,900</dd>
    </dl>
</article>
```

### FAQ 頁面
```html
<article>
    <h2>常見問題</h2>

    <dl>
        <dt>Q1: 如何建立帳號？</dt>
        <dd>
            <p>請按照以下步驟註冊：</p>
            <ol>
                <li>點擊右上角「註冊」按鈕</li>
                <li>填寫電子郵件和密碼</li>
                <li>驗證郵件信箱</li>
                <li>完成個人資料設定</li>
            </ol>
        </dd>

        <dt>Q2: 支援哪些付款方式？</dt>
        <dd>
            <p>我們支援以下付款方式：</p>
            <ul>
                <li>信用卡（Visa、Mastercard、JCB）</li>
                <li>ATM 轉帳</li>
                <li>超商代碼繳費</li>
                <li>行動支付（Apple Pay、Google Pay）</li>
            </ul>
        </dd>

        <dt>Q3: 運送需要多久時間？</dt>
        <dd>
            一般情況下：
        </dd>
        <dd>台灣本島：2-3 個工作天</dd>
        <dd>離島地區：3-5 個工作天</dd>
        <dd>國際運送：7-14 個工作天</dd>
    </dl>
</article>
```

### 待辦清單
```html
<article>
    <h2>今日待辦事項</h2>

    <h3>工作</h3>
    <ul>
        <li>
            <input type="checkbox" id="task1" checked>
            <label for="task1">完成專案報告</label>
        </li>
        <li>
            <input type="checkbox" id="task2">
            <label for="task2">回覆客戶郵件</label>
        </li>
        <li>
            <input type="checkbox" id="task3">
            <label for="task3">參加團隊會議</label>
        </li>
    </ul>

    <h3>個人</h3>
    <ul>
        <li>
            <input type="checkbox" id="task4">
            <label for="task4">購買日用品</label>
        </li>
        <li>
            <input type="checkbox" id="task5">
            <label for="task5">運動 30 分鐘</label>
        </li>
    </ul>
</article>
```

### 食譜範例
```html
<article>
    <h2>經典番茄義大利麵</h2>

    <section>
        <h3>材料（2人份）</h3>
        <ul>
            <li>義大利麵 200 克</li>
            <li>新鮮番茄 4 顆</li>
            <li>大蒜 3 瓣</li>
            <li>橄欖油 2 大匙</li>
            <li>羅勒葉 適量</li>
            <li>鹽、黑胡椒 適量</li>
        </ul>
    </section>

    <section>
        <h3>烹飪步驟</h3>
        <ol>
            <li>
                <strong>準備材料</strong>
                <ul>
                    <li>番茄切丁</li>
                    <li>大蒜切末</li>
                    <li>羅勒葉撕碎</li>
                </ul>
            </li>
            <li>
                <strong>煮義大利麵</strong>
                <ul>
                    <li>煮沸一大鍋水</li>
                    <li>加入鹽</li>
                    <li>放入義大利麵，煮 8-10 分鐘至彈牙</li>
                </ul>
            </li>
            <li>
                <strong>製作醬汁</strong>
                <ul>
                    <li>熱鍋加橄欖油</li>
                    <li>爆香蒜末</li>
                    <li>加入番茄丁翻炒</li>
                    <li>調味並煮至濃稠</li>
                </ul>
            </li>
            <li>
                <strong>混合與上菜</strong>
                <ul>
                    <li>將煮好的麵條瀝乾</li>
                    <li>與醬汁混合</li>
                    <li>撒上羅勒葉</li>
                    <li>趁熱享用</li>
                </ul>
            </li>
        </ol>
    </section>

    <section>
        <h3>烹飪小技巧</h3>
        <dl>
            <dt>如何讓義大利麵更有嚼勁？</dt>
            <dd>煮麵時不要煮過頭，保持「彈牙」（al dente）口感</dd>

            <dt>醬汁太酸怎麼辦？</dt>
            <dd>可以加入少許糖中和酸味</dd>

            <dt>沒有新鮮番茄可以用什麼代替？</dt>
            <dd>可使用番茄罐頭或番茄糊</dd>
        </dl>
    </section>
</article>
```

---

## 最佳實踐總結

### 選擇正確的列表類型

| 情境 | 使用標籤 | 原因 |
|------|---------|------|
| 項目無順序關係 | `<ul>` | 無序列表 |
| 項目有順序或優先級 | `<ol>` | 有序列表 |
| 術語和定義配對 | `<dl>` + `<dt>` + `<dd>` | 描述列表 |
| 導航選單 | `<nav>` + `<ul>` | 語意化導航 |
| 麵包屑導航 | `<nav>` + `<ol>` | 有順序的導航 |

### ✅ 最佳實踐
1. 根據內容語意選擇列表類型
2. 使用 CSS 控制樣式，不使用廢棄屬性
3. 為導航列表加上 `<nav>` 和 `aria-label`
4. 確保列表有正確的層級結構
5. `<dl>` 只包含 `<dt>` 和 `<dd>`
6. `<ul>` 和 `<ol>` 只包含 `<li>`

### ❌ 常見錯誤
1. 為了縮排而使用列表（應使用 CSS）
2. 手動添加編號而非使用 `<ol>`
3. 在列表標籤內直接放文字（應放在 `<li>` 內）
4. 錯誤的巢狀結構
5. 使用已廢棄的屬性

### 無障礙建議
- ✅ 螢幕閱讀器會宣告列表類型和項目總數
- ✅ 使用適當的 ARIA 標籤（如 `role="navigation"`）
- ✅ 確保鍵盤可以導航列表中的連結
- ✅ 為複雜列表提供說明文字

---

[⬆️ 回到頂部](#列表標籤) | [📑 回索引頁](index.md)
