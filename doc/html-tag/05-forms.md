# 表單標籤 (Forms)

> 表單標籤用於建立互動式表單，收集使用者輸入的資料。HTML5 提供了豐富的表單控制項和驗證功能。

## 📑 目錄

- [`<form>` - 表單容器](#form---表單容器)
- [`<input>` - 輸入欄位](#input---輸入欄位)
  - [type="text" - 文字輸入](#typetext---文字輸入)
  - [type="password" - 密碼輸入](#typepassword---密碼輸入)
  - [type="email" - 電子郵件](#typeemail---電子郵件)
  - [type="number" - 數字輸入](#typenumber---數字輸入)
  - [type="tel" - 電話號碼](#typetel---電話號碼)
  - [type="url" - 網址](#typeurl---網址)
  - [type="search" - 搜尋](#typesearch---搜尋)
  - [type="date" - 日期選擇](#typedate---日期選擇)
  - [type="time" - 時間選擇](#typetime---時間選擇)
  - [type="datetime-local" - 日期時間](#typedatetime-local---日期時間)
  - [type="month" - 月份選擇](#typemonth---月份選擇)
  - [type="week" - 週數選擇](#typeweek---週數選擇)
  - [type="color" - 顏色選擇](#typecolor---顏色選擇)
  - [type="checkbox" - 核取方塊](#typecheckbox---核取方塊)
  - [type="radio" - 單選按鈕](#typeradio---單選按鈕)
  - [type="file" - 檔案上傳](#typefile---檔案上傳)
  - [type="range" - 滑桿](#typerange---滑桿)
  - [type="submit" - 提交按鈕](#typesubmit---提交按鈕)
  - [type="reset" - 重置按鈕](#typereset---重置按鈕)
  - [type="button" - 一般按鈕](#typebutton---一般按鈕)
  - [type="hidden" - 隱藏欄位](#typehidden---隱藏欄位)
  - [type="image" - 圖片按鈕](#typeimage---圖片按鈕)
- [`<textarea>` - 多行文字輸入](#textarea---多行文字輸入)
- [`<select>` - 下拉選單](#select---下拉選單)
- [`<option>` - 選項](#option---選項)
- [`<optgroup>` - 選項群組](#optgroup---選項群組)
- [`<button>` - 按鈕](#button---按鈕)
- [`<label>` - 標籤](#label---標籤)
- [`<fieldset>` - 表單欄位群組](#fieldset---表單欄位群組)
- [`<legend>` - 群組標題](#legend---群組標題)
- [`<datalist>` - 資料清單](#datalist---資料清單)
- [`<output>` - 輸出結果](#output---輸出結果)
- [`<progress>` - 進度條](#progress---進度條)
- [`<meter>` - 測量儀表](#meter---測量儀表)
- [實際應用範例](#實際應用範例)
  - [登入表單](#登入表單)
  - [註冊表單](#註冊表單)
  - [聯絡表單](#聯絡表單)
  - [搜尋表單](#搜尋表單)
  - [訂單表單](#訂單表單)
- [表單驗證](#表單驗證)
- [最佳實踐總結](#最佳實踐總結)

---

## `<form>` - 表單容器

### 說明
`<form>` 標籤用於建立 HTML 表單，作為所有表單控制項的容器。表單可以將使用者輸入的資料提交到伺服器進行處理。

### 語法
```html
<form action="URL" method="POST/GET">
  <!-- 表單控制項 -->
</form>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `action` | 表單提交的目標 URL | URL | 否 |
| `method` | HTTP 提交方法 | `GET`, `POST` | 否 (預設 GET) |
| `enctype` | 表單資料編碼方式 | `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` | 否 |
| `name` | 表單名稱 | 文字 | 否 |
| `target` | 回應顯示位置 | `_self`, `_blank`, `_parent`, `_top` | 否 |
| `autocomplete` | 自動完成功能 | `on`, `off` | 否 |
| `novalidate` | 停用表單驗證 | 布林值 | 否 |

### 📌 程式碼範例

```html
<!-- 基本表單 -->
<form action="/submit" method="POST">
  <label for="username">使用者名稱:</label>
  <input type="text" id="username" name="username">
  <button type="submit">提交</button>
</form>

<!-- 檔案上傳表單 -->
<form action="/upload" method="POST" enctype="multipart/form-data">
  <label for="file">選擇檔案:</label>
  <input type="file" id="file" name="file">
  <button type="submit">上傳</button>
</form>

<!-- 關閉自動完成 -->
<form action="/login" method="POST" autocomplete="off">
  <label for="password">密碼:</label>
  <input type="password" id="password" name="password">
  <button type="submit">登入</button>
</form>
```

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 使用有意義的 `name` 屬性
- ✅ 為每個輸入欄位提供對應的 `<label>`
- ✅ 使用 `fieldset` 和 `legend` 組織相關欄位
- ✅ 提供明確的錯誤訊息
- ⚠️ 避免使用 `novalidate` 除非有自訂驗證

### 使用注意事項

```html
<!-- ❌ 錯誤：表單巢狀 -->
<form action="/outer">
  <form action="/inner">
    <!-- 不允許表單巢狀 -->
  </form>
</form>

<!-- ✅ 正確：使用 form 屬性關聯 -->
<form id="myForm" action="/submit"></form>
<input type="text" name="field" form="myForm">
```

---

## `<input>` - 輸入欄位

### 說明
`<input>` 是最常用的表單元素，透過不同的 `type` 屬性可以建立各種輸入控制項。

### 語法
```html
<input type="類型" name="名稱" value="值">
```

### 通用屬性

| 屬性 | 說明 | 適用類型 |
|------|------|----------|
| `name` | 欄位名稱（提交時使用） | 所有 |
| `value` | 預設值 | 所有 |
| `placeholder` | 提示文字 | text, password, email, tel, url, search, number |
| `required` | 必填欄位 | 多數類型 |
| `disabled` | 停用欄位 | 所有 |
| `readonly` | 唯讀欄位 | text, password, email 等 |
| `autofocus` | 自動聚焦 | 所有 |
| `autocomplete` | 自動完成 | text, password, email 等 |
| `pattern` | 正規表達式驗證 | text, password, email, tel, url, search |
| `maxlength` | 最大字元長度 | text, password, email, tel, url, search |
| `minlength` | 最小字元長度 | text, password, email, tel, url, search |
| `min` | 最小值 | number, date, time, range |
| `max` | 最大值 | number, date, time, range |
| `step` | 數值間隔 | number, range, date, time |
| `multiple` | 允許多選 | email, file |
| `accept` | 可接受的檔案類型 | file |
| `checked` | 預設勾選 | checkbox, radio |

---

### type="text" - 文字輸入

#### 說明
最基本的文字輸入欄位，用於輸入單行文字。

#### 📌 程式碼範例

```html
<!-- 基本文字輸入 -->
<label for="name">姓名:</label>
<input type="text" id="name" name="name" placeholder="請輸入您的姓名">

<!-- 有最大長度限制 -->
<label for="username">使用者名稱:</label>
<input type="text" id="username" name="username" maxlength="20" required>

<!-- 有預設值 -->
<label for="city">城市:</label>
<input type="text" id="city" name="city" value="台北">

<!-- 使用 pattern 驗證 -->
<label for="code">產品代碼 (格式: ABC-1234):</label>
<input type="text" id="code" name="code" pattern="[A-Z]{3}-\d{4}"
       placeholder="ABC-1234" title="請輸入格式: ABC-1234">
```

#### ✨ 示範效果

<label for="demo-text">文字輸入:</label>
<input type="text" id="demo-text" placeholder="請輸入文字">

---

### type="password" - 密碼輸入

#### 說明
密碼輸入欄位，輸入的內容會被遮罩顯示。

#### 📌 程式碼範例

```html
<!-- 基本密碼輸入 -->
<label for="password">密碼:</label>
<input type="password" id="password" name="password" required>

<!-- 有最小長度要求 -->
<label for="new-password">新密碼 (至少 8 個字元):</label>
<input type="password" id="new-password" name="new-password"
       minlength="8" required>

<!-- 密碼強度要求 -->
<label for="strong-password">強密碼:</label>
<input type="password" id="strong-password" name="strong-password"
       pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}"
       title="至少 8 個字元，包含大小寫字母和數字">
```

#### ✨ 示範效果

<label for="demo-password">密碼:</label>
<input type="password" id="demo-password" placeholder="請輸入密碼">

---

### type="email" - 電子郵件

#### 說明
專門用於輸入電子郵件地址，瀏覽器會自動驗證格式。

#### 📌 程式碼範例

```html
<!-- 基本 email 輸入 -->
<label for="email">電子郵件:</label>
<input type="email" id="email" name="email" required>

<!-- 多個 email -->
<label for="emails">多個電子郵件 (用逗號分隔):</label>
<input type="email" id="emails" name="emails" multiple>

<!-- 有提示文字 -->
<label for="work-email">公司信箱:</label>
<input type="email" id="work-email" name="work-email"
       placeholder="user@company.com">
```

#### ✨ 示範效果

<label for="demo-email">電子郵件:</label>
<input type="email" id="demo-email" placeholder="example@mail.com">

---

### type="number" - 數字輸入

#### 說明
用於輸入數字，支援最小值、最大值和間隔設定。

#### 📌 程式碼範例

```html
<!-- 基本數字輸入 -->
<label for="age">年齡:</label>
<input type="number" id="age" name="age" min="0" max="120">

<!-- 有間隔的數字 -->
<label for="quantity">數量 (5 的倍數):</label>
<input type="number" id="quantity" name="quantity" min="0" step="5" value="10">

<!-- 小數 -->
<label for="price">價格:</label>
<input type="number" id="price" name="price" min="0" step="0.01" placeholder="0.00">
```

#### ✨ 示範效果

<label for="demo-number">數量:</label>
<input type="number" id="demo-number" min="1" max="100" value="1">

---

### type="tel" - 電話號碼

#### 說明
用於輸入電話號碼，在行動裝置上會顯示數字鍵盤。

#### 📌 程式碼範例

```html
<!-- 基本電話輸入 -->
<label for="phone">電話:</label>
<input type="tel" id="phone" name="phone">

<!-- 台灣電話格式 -->
<label for="tw-phone">手機號碼:</label>
<input type="tel" id="tw-phone" name="tw-phone"
       pattern="09\d{8}"
       placeholder="0912345678"
       title="請輸入台灣手機號碼格式">

<!-- 市話格式 -->
<label for="landline">市內電話:</label>
<input type="tel" id="landline" name="landline"
       pattern="\d{2,3}-\d{7,8}"
       placeholder="02-12345678">
```

#### ✨ 示範效果

<label for="demo-tel">電話:</label>
<input type="tel" id="demo-tel" placeholder="0912345678">

---

### type="url" - 網址

#### 說明
用於輸入 URL，瀏覽器會驗證是否為有效的網址格式。

#### 📌 程式碼範例

```html
<!-- 基本 URL 輸入 -->
<label for="website">網站:</label>
<input type="url" id="website" name="website" placeholder="https://example.com">

<!-- 必填的網址 -->
<label for="homepage">個人網站:</label>
<input type="url" id="homepage" name="homepage" required>
```

#### ✨ 示範效果

<label for="demo-url">網址:</label>
<input type="url" id="demo-url" placeholder="https://example.com">

---

### type="search" - 搜尋

#### 說明
用於搜尋輸入欄位，某些瀏覽器會提供清除按鈕。

#### 📌 程式碼範例

```html
<!-- 基本搜尋 -->
<label for="search">搜尋:</label>
<input type="search" id="search" name="search" placeholder="輸入關鍵字...">

<!-- 有建議的搜尋 -->
<label for="search-suggest">搜尋:</label>
<input type="search" id="search-suggest" name="q" list="suggestions">
<datalist id="suggestions">
  <option value="HTML">
  <option value="CSS">
  <option value="JavaScript">
</datalist>
```

#### ✨ 示範效果

<label for="demo-search">搜尋:</label>
<input type="search" id="demo-search" placeholder="搜尋...">

---

### type="date" - 日期選擇

#### 說明
提供日期選擇器，讓使用者選擇日期。

#### 📌 程式碼範例

```html
<!-- 基本日期 -->
<label for="birthday">生日:</label>
<input type="date" id="birthday" name="birthday">

<!-- 有最小和最大日期限制 -->
<label for="appointment">預約日期 (未來 30 天內):</label>
<input type="date" id="appointment" name="appointment"
       min="2026-01-02" max="2026-02-01">

<!-- 預設為今天 -->
<label for="today">日期:</label>
<input type="date" id="today" name="today" value="2026-01-02">
```

#### ✨ 示範效果

<label for="demo-date">日期:</label>
<input type="date" id="demo-date">

---

### type="time" - 時間選擇

#### 說明
提供時間選擇器，讓使用者選擇時間。

#### 📌 程式碼範例

```html
<!-- 基本時間 -->
<label for="time">時間:</label>
<input type="time" id="time" name="time">

<!-- 營業時間限制 -->
<label for="business-hours">營業時間 (09:00-18:00):</label>
<input type="time" id="business-hours" name="business-hours"
       min="09:00" max="18:00">

<!-- 以 30 分鐘為間隔 -->
<label for="meeting-time">會議時間:</label>
<input type="time" id="meeting-time" name="meeting-time" step="1800">
```

#### ✨ 示範效果

<label for="demo-time">時間:</label>
<input type="time" id="demo-time">

---

### type="datetime-local" - 日期時間

#### 說明
結合日期和時間的選擇器。

#### 📌 程式碼範例

```html
<!-- 基本日期時間 -->
<label for="datetime">日期和時間:</label>
<input type="datetime-local" id="datetime" name="datetime">

<!-- 預約日期時間 -->
<label for="reservation">預約時間:</label>
<input type="datetime-local" id="reservation" name="reservation"
       min="2026-01-02T00:00" required>
```

#### ✨ 示範效果

<label for="demo-datetime">日期時間:</label>
<input type="datetime-local" id="demo-datetime">

---

### type="month" - 月份選擇

#### 說明
讓使用者選擇年份和月份。

#### 📌 程式碼範例

```html
<!-- 基本月份選擇 -->
<label for="month">選擇月份:</label>
<input type="month" id="month" name="month">

<!-- 限制在今年 -->
<label for="this-year">本年度月份:</label>
<input type="month" id="this-year" name="this-year"
       min="2026-01" max="2026-12">
```

#### ✨ 示範效果

<label for="demo-month">月份:</label>
<input type="month" id="demo-month">

---

### type="week" - 週數選擇

#### 說明
讓使用者選擇年份和週數。

#### 📌 程式碼範例

```html
<!-- 基本週數選擇 -->
<label for="week">選擇週:</label>
<input type="week" id="week" name="week">
```

#### ✨ 示範效果

<label for="demo-week">週數:</label>
<input type="week" id="demo-week">

---

### type="color" - 顏色選擇

#### 說明
提供顏色選擇器，讓使用者選擇顏色。

#### 📌 程式碼範例

```html
<!-- 基本顏色選擇 -->
<label for="color">選擇顏色:</label>
<input type="color" id="color" name="color">

<!-- 預設顏色 -->
<label for="theme-color">主題顏色:</label>
<input type="color" id="theme-color" name="theme-color" value="#ff6600">
```

#### ✨ 示範效果

<label for="demo-color">顏色:</label>
<input type="color" id="demo-color" value="#3b82f6">

---

### type="checkbox" - 核取方塊

#### 說明
允許使用者選擇一個或多個選項。

#### 📌 程式碼範例

```html
<!-- 單一核取方塊 -->
<label>
  <input type="checkbox" name="agree" value="yes" required>
  我同意服務條款
</label>

<!-- 多個核取方塊 -->
<fieldset>
  <legend>興趣：</legend>
  <label><input type="checkbox" name="interests" value="sports"> 運動</label>
  <label><input type="checkbox" name="interests" value="music"> 音樂</label>
  <label><input type="checkbox" name="interests" value="reading"> 閱讀</label>
  <label><input type="checkbox" name="interests" value="travel"> 旅遊</label>
</fieldset>

<!-- 預設勾選 -->
<label>
  <input type="checkbox" name="newsletter" value="yes" checked>
  訂閱電子報
</label>
```

#### ✨ 示範效果

<fieldset style="border: 1px solid #ccc; padding: 10px;">
  <legend>選擇您的興趣：</legend>
  <label><input type="checkbox" name="demo-interests" value="sports"> 運動</label><br>
  <label><input type="checkbox" name="demo-interests" value="music"> 音樂</label><br>
  <label><input type="checkbox" name="demo-interests" value="reading" checked> 閱讀</label>
</fieldset>

---

### type="radio" - 單選按鈕

#### 說明
允許使用者從多個選項中選擇一個。同一組的 radio 必須有相同的 `name`。

#### 📌 程式碼範例

```html
<!-- 基本單選 -->
<fieldset>
  <legend>性別：</legend>
  <label><input type="radio" name="gender" value="male" required> 男性</label>
  <label><input type="radio" name="gender" value="female"> 女性</label>
  <label><input type="radio" name="gender" value="other"> 其他</label>
</fieldset>

<!-- 預設選項 -->
<fieldset>
  <legend>配送方式：</legend>
  <label><input type="radio" name="shipping" value="standard" checked> 標準配送 (免費)</label>
  <label><input type="radio" name="shipping" value="express"> 快速配送 (+$100)</label>
</fieldset>
```

#### ✨ 示範效果

<fieldset style="border: 1px solid #ccc; padding: 10px;">
  <legend>選擇付款方式：</legend>
  <label><input type="radio" name="demo-payment" value="credit" checked> 信用卡</label><br>
  <label><input type="radio" name="demo-payment" value="atm"> ATM 轉帳</label><br>
  <label><input type="radio" name="demo-payment" value="cod"> 貨到付款</label>
</fieldset>

---

### type="file" - 檔案上傳

#### 說明
允許使用者上傳檔案。

#### 📌 程式碼範例

```html
<!-- 基本檔案上傳 -->
<label for="file">選擇檔案:</label>
<input type="file" id="file" name="file">

<!-- 限制檔案類型 -->
<label for="image">上傳圖片 (JPG, PNG):</label>
<input type="file" id="image" name="image" accept="image/jpeg,image/png">

<!-- 多檔案上傳 -->
<label for="documents">上傳多個文件:</label>
<input type="file" id="documents" name="documents" multiple>

<!-- 只接受圖片 -->
<label for="avatar">頭像:</label>
<input type="file" id="avatar" name="avatar" accept="image/*">
```

#### ✨ 示範效果

<label for="demo-file">選擇檔案:</label>
<input type="file" id="demo-file">

---

### type="range" - 滑桿

#### 說明
提供滑桿控制項，讓使用者選擇範圍內的數值。

#### 📌 程式碼範例

```html
<!-- 基本滑桿 -->
<label for="volume">音量:</label>
<input type="range" id="volume" name="volume" min="0" max="100" value="50">

<!-- 顯示目前值 -->
<label for="brightness">亮度: <span id="brightness-value">50</span>%</label>
<input type="range" id="brightness" name="brightness" min="0" max="100" value="50"
       oninput="document.getElementById('brightness-value').textContent = this.value">

<!-- 自訂間隔 -->
<label for="rating">評分 (1-5):</label>
<input type="range" id="rating" name="rating" min="1" max="5" step="1" value="3">
```

#### ✨ 示範效果

<label for="demo-range">音量: <span id="demo-range-value">50</span></label><br>
<input type="range" id="demo-range" min="0" max="100" value="50"
       oninput="document.getElementById('demo-range-value').textContent = this.value">

---

### type="submit" - 提交按鈕

#### 說明
提交表單的按鈕。

#### 📌 程式碼範例

```html
<!-- 基本提交按鈕 -->
<input type="submit" value="提交">

<!-- 自訂文字 -->
<input type="submit" value="立即註冊">

<!-- 停用狀態 -->
<input type="submit" value="處理中..." disabled>
```

#### ✨ 示範效果

<input type="submit" value="提交表單">

---

### type="reset" - 重置按鈕

#### 說明
重置表單到初始狀態的按鈕。

#### 📌 程式碼範例

```html
<!-- 基本重置按鈕 -->
<input type="reset" value="重置">

<!-- 自訂文字 -->
<input type="reset" value="清除所有欄位">
```

#### ✨ 示範效果

<input type="reset" value="重置表單">

---

### type="button" - 一般按鈕

#### 說明
一般按鈕，沒有預設行為，通常配合 JavaScript 使用。

#### 📌 程式碼範例

```html
<!-- 基本按鈕 -->
<input type="button" value="點擊我" onclick="alert('按鈕被點擊了！')">

<!-- 自訂功能 -->
<input type="button" value="顯示/隱藏" onclick="toggleVisibility()">
```

#### ✨ 示範效果

<input type="button" value="點擊測試" onclick="alert('這是一個測試按鈕！')">

---

### type="hidden" - 隱藏欄位

#### 說明
隱藏欄位，不會顯示在頁面上，但會隨表單一起提交。

#### 📌 程式碼範例

```html
<!-- 隱藏的使用者 ID -->
<input type="hidden" name="user_id" value="12345">

<!-- CSRF token -->
<input type="hidden" name="csrf_token" value="abc123xyz789">

<!-- 追蹤資訊 -->
<input type="hidden" name="source" value="email-campaign">
```

---

### type="image" - 圖片按鈕

#### 說明
使用圖片作為提交按鈕。

#### 📌 程式碼範例

```html
<!-- 圖片提交按鈕 -->
<input type="image" src="submit-button.png" alt="提交">

<!-- 有寬高的圖片按鈕 -->
<input type="image" src="search-icon.png" alt="搜尋" width="32" height="32">
```

---

## `<textarea>` - 多行文字輸入

### 說明
`<textarea>` 用於輸入多行文字，適合較長的文字內容如評論、訊息等。

### 語法
```html
<textarea name="名稱" rows="列數" cols="欄數">預設內容</textarea>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `name` | 欄位名稱 | 文字 | 否 |
| `rows` | 可見列數 | 數字 | 否 |
| `cols` | 可見欄數 | 數字 | 否 |
| `placeholder` | 提示文字 | 文字 | 否 |
| `maxlength` | 最大字元數 | 數字 | 否 |
| `minlength` | 最小字元數 | 數字 | 否 |
| `required` | 必填欄位 | 布林值 | 否 |
| `readonly` | 唯讀 | 布林值 | 否 |
| `disabled` | 停用 | 布林值 | 否 |
| `wrap` | 換行方式 | `soft`, `hard` | 否 |

### 📌 程式碼範例

```html
<!-- 基本多行輸入 -->
<label for="message">訊息:</label>
<textarea id="message" name="message" rows="5" cols="50"></textarea>

<!-- 有提示文字 -->
<label for="comment">留言:</label>
<textarea id="comment" name="comment" rows="4"
          placeholder="請輸入您的留言..."></textarea>

<!-- 有字數限制 -->
<label for="bio">個人簡介 (最多 200 字):</label>
<textarea id="bio" name="bio" rows="4" maxlength="200" required></textarea>

<!-- 有預設內容 -->
<label for="description">描述:</label>
<textarea id="description" name="description" rows="3">這是預設內容</textarea>

<!-- 固定大小（禁止調整） -->
<textarea style="resize: none;" rows="3" cols="40">無法調整大小</textarea>
```

### ✨ 示範效果

<label for="demo-textarea">您的意見:</label><br>
<textarea id="demo-textarea" rows="4" cols="50" placeholder="請輸入您的意見..."></textarea>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 使用 `<label>` 標籤關聯
- ✅ 提供明確的 `placeholder` 提示
- ✅ 使用 `maxlength` 告知字數限制
- ⚠️ 避免設定過小的 `rows` 和 `cols`

### 使用注意事項

```html
<!-- ❌ 錯誤：使用 value 屬性 -->
<textarea value="錯誤"></textarea>

<!-- ✅ 正確：內容放在標籤之間 -->
<textarea>正確</textarea>

<!-- ❌ 錯誤：過小的尺寸 -->
<textarea rows="1" cols="10"></textarea>

<!-- ✅ 正確：適當的尺寸 -->
<textarea rows="4" cols="50"></textarea>
```

---

## `<select>` - 下拉選單

### 說明
`<select>` 建立下拉選單，讓使用者從選項中選擇。

### 語法
```html
<select name="名稱">
  <option value="值">選項文字</option>
</select>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `name` | 欄位名稱 | 文字 | 否 |
| `multiple` | 允許多選 | 布林值 | 否 |
| `size` | 可見選項數 | 數字 | 否 |
| `required` | 必選 | 布林值 | 否 |
| `disabled` | 停用 | 布林值 | 否 |
| `autofocus` | 自動聚焦 | 布林值 | 否 |

### 📌 程式碼範例

```html
<!-- 基本下拉選單 -->
<label for="country">國家:</label>
<select id="country" name="country">
  <option value="">請選擇</option>
  <option value="tw">台灣</option>
  <option value="jp">日本</option>
  <option value="us">美國</option>
</select>

<!-- 預設選項 -->
<label for="language">語言:</label>
<select id="language" name="language">
  <option value="zh-TW" selected>繁體中文</option>
  <option value="en">English</option>
  <option value="ja">日本語</option>
</select>

<!-- 多選（按住 Ctrl 可多選） -->
<label for="colors">喜歡的顏色 (可多選):</label>
<select id="colors" name="colors" multiple size="4">
  <option value="red">紅色</option>
  <option value="blue">藍色</option>
  <option value="green">綠色</option>
  <option value="yellow">黃色</option>
</select>

<!-- 必選欄位 -->
<label for="category">分類:</label>
<select id="category" name="category" required>
  <option value="">-- 請選擇分類 --</option>
  <option value="tech">科技</option>
  <option value="sports">運動</option>
  <option value="music">音樂</option>
</select>
```

### ✨ 示範效果

<label for="demo-select">選擇城市:</label>
<select id="demo-select">
  <option value="">請選擇</option>
  <option value="taipei">台北</option>
  <option value="taichung">台中</option>
  <option value="kaohsiung">高雄</option>
</select>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 第一個選項使用空值 `value=""` 作為提示
- ✅ 使用 `<label>` 標籤
- ✅ 對於必選欄位使用 `required`
- ✅ 使用 `<optgroup>` 組織選項
- ⚠️ 多選時使用 `size` 顯示多個選項

---

## `<option>` - 選項

### 說明
`<option>` 定義下拉選單或列表中的選項。

### 語法
```html
<option value="值">顯示文字</option>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `value` | 選項值（提交時使用） | 文字 | 否 |
| `selected` | 預設選中 | 布林值 | 否 |
| `disabled` | 停用選項 | 布林值 | 否 |
| `label` | 選項標籤 | 文字 | 否 |

### 📌 程式碼範例

```html
<select name="priority">
  <option value="">選擇優先級</option>
  <option value="low">低</option>
  <option value="medium" selected>中</option>
  <option value="high">高</option>
  <option value="urgent" disabled>緊急 (暫時關閉)</option>
</select>
```

### 使用注意事項

```html
<!-- ❌ 錯誤：沒有 value，會提交顯示文字 -->
<option>台北</option>

<!-- ✅ 正確：明確指定 value -->
<option value="taipei">台北</option>

<!-- ✅ 正確：value 和顯示文字可以不同 -->
<option value="tw-tpe">台北 (Taipei)</option>
```

---

## `<optgroup>` - 選項群組

### 說明
`<optgroup>` 用於將 `<select>` 中的選項分組。

### 語法
```html
<optgroup label="群組名稱">
  <option>選項</option>
</optgroup>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `label` | 群組標籤 | 文字 | 是 |
| `disabled` | 停用整個群組 | 布林值 | 否 |

### 📌 程式碼範例

```html
<label for="car">選擇車款:</label>
<select id="car" name="car">
  <option value="">請選擇</option>

  <optgroup label="日系品牌">
    <option value="toyota">Toyota</option>
    <option value="honda">Honda</option>
    <option value="nissan">Nissan</option>
  </optgroup>

  <optgroup label="歐系品牌">
    <option value="bmw">BMW</option>
    <option value="benz">Mercedes-Benz</option>
    <option value="audi">Audi</option>
  </optgroup>

  <optgroup label="美系品牌" disabled>
    <option value="ford">Ford</option>
    <option value="chevrolet">Chevrolet</option>
  </optgroup>
</select>
```

### ✨ 示範效果

<label for="demo-optgroup">選擇水果:</label>
<select id="demo-optgroup">
  <optgroup label="熱帶水果">
    <option>芒果</option>
    <option>鳳梨</option>
    <option>香蕉</option>
  </optgroup>
  <optgroup label="溫帶水果">
    <option>蘋果</option>
    <option>梨子</option>
    <option>櫻桃</option>
  </optgroup>
</select>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ 6+ |

---

## `<button>` - 按鈕

### 說明
`<button>` 建立可點擊的按鈕，比 `<input type="button">` 更靈活，可以包含 HTML 內容。

### 語法
```html
<button type="類型">按鈕文字</button>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `type` | 按鈕類型 | `button`, `submit`, `reset` | 否 (預設 submit) |
| `name` | 按鈕名稱 | 文字 | 否 |
| `value` | 按鈕值 | 文字 | 否 |
| `disabled` | 停用按鈕 | 布林值 | 否 |
| `autofocus` | 自動聚焦 | 布林值 | 否 |
| `form` | 關聯的表單 ID | ID | 否 |

### 📌 程式碼範例

```html
<!-- 提交按鈕 -->
<button type="submit">提交表單</button>

<!-- 一般按鈕 -->
<button type="button" onclick="alert('Hello!')">點擊我</button>

<!-- 重置按鈕 -->
<button type="reset">重置</button>

<!-- 包含圖示的按鈕 -->
<button type="submit">
  <img src="icon-send.png" alt="" width="16" height="16">
  發送訊息
</button>

<!-- 停用狀態 -->
<button type="submit" disabled>處理中...</button>

<!-- 按鈕在表單外 -->
<form id="myForm" action="/submit">
  <input type="text" name="data">
</form>
<button type="submit" form="myForm">提交</button>
```

### ✨ 示範效果

<button type="button">一般按鈕</button>
<button type="submit">提交按鈕</button>
<button type="reset">重置按鈕</button>
<button type="button" disabled>停用按鈕</button>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 使用清楚的按鈕文字
- ✅ 重要按鈕使用明確的 `type` 屬性
- ✅ 停用時提供視覺回饋
- ⚠️ 避免只用圖示而無文字說明

### 使用注意事項

```html
<!-- ❌ 錯誤：在表單中沒指定 type，預設為 submit -->
<form>
  <button onclick="doSomething()">按鈕</button> <!-- 會提交表單！ -->
</form>

<!-- ✅ 正確：明確指定 type="button" -->
<form>
  <button type="button" onclick="doSomething()">按鈕</button>
</form>

<!-- ❌ 錯誤：按鈕內容過於複雜 -->
<button>
  <div>
    <form>...</form> <!-- 不可在按鈕內放表單 -->
  </div>
</button>

<!-- ✅ 正確：簡單的內容 -->
<button>
  <span class="icon">📧</span> 發送郵件
</button>
```

---

## `<label>` - 標籤

### 說明
`<label>` 為表單元素定義標籤，提升無障礙性和使用者體驗。點擊標籤會聚焦到對應的輸入欄位。

### 語法
```html
<!-- 方法 1: 使用 for 屬性 -->
<label for="input-id">標籤文字</label>
<input id="input-id" type="text">

<!-- 方法 2: 包裹輸入元素 -->
<label>
  標籤文字
  <input type="text">
</label>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `for` | 關聯的表單元素 ID | ID | 否 |

### 📌 程式碼範例

```html
<!-- 使用 for 屬性 -->
<label for="username">使用者名稱:</label>
<input type="text" id="username" name="username">

<!-- 包裹方式 -->
<label>
  電子郵件:
  <input type="email" name="email">
</label>

<!-- checkbox 的標籤 -->
<label for="agree">
  <input type="checkbox" id="agree" name="agree">
  我同意服務條款
</label>

<!-- 或者 -->
<label>
  <input type="checkbox" name="newsletter">
  訂閱電子報
</label>

<!-- 必填欄位標示 -->
<label for="password">
  密碼 <span style="color: red;">*</span>
</label>
<input type="password" id="password" name="password" required>
```

### ✨ 示範效果

<label for="demo-label-input">點擊此標籤會聚焦到輸入欄位:</label><br>
<input type="text" id="demo-label-input" placeholder="試試點擊上方標籤">

<br><br>

<label>
  <input type="checkbox"> 包裹方式的 checkbox
</label>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 每個輸入欄位都應該有對應的 `<label>`
- ✅ 使用 `for` 屬性明確關聯
- ✅ 標籤文字要清楚明確
- ✅ 必填欄位要有視覺標示 (如 `*`)
- ⚠️ 不要省略 `<label>`，即使有 `placeholder`

### 使用注意事項

```html
<!-- ❌ 錯誤：只用 placeholder，沒有 label -->
<input type="text" placeholder="使用者名稱">

<!-- ✅ 正確：同時有 label 和 placeholder -->
<label for="user">使用者名稱:</label>
<input type="text" id="user" placeholder="請輸入使用者名稱">

<!-- ❌ 錯誤：for 對應錯誤的 ID -->
<label for="email">姓名:</label>
<input type="text" id="name" name="name">

<!-- ✅ 正確：for 對應正確的 ID -->
<label for="name">姓名:</label>
<input type="text" id="name" name="name">
```

---

## `<fieldset>` - 表單欄位群組

### 說明
`<fieldset>` 將相關的表單元素組合在一起，並繪製邊框。

### 語法
```html
<fieldset>
  <legend>群組標題</legend>
  <!-- 表單元素 -->
</fieldset>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `disabled` | 停用整個群組 | 布林值 | 否 |
| `form` | 關聯的表單 ID | ID | 否 |
| `name` | 群組名稱 | 文字 | 否 |

### 📌 程式碼範例

```html
<!-- 基本 fieldset -->
<fieldset>
  <legend>個人資訊</legend>
  <label for="first-name">名字:</label>
  <input type="text" id="first-name" name="first-name"><br>

  <label for="last-name">姓氏:</label>
  <input type="text" id="last-name" name="last-name">
</fieldset>

<!-- 單選按鈕群組 -->
<fieldset>
  <legend>配送方式</legend>
  <label><input type="radio" name="shipping" value="standard"> 標準配送</label><br>
  <label><input type="radio" name="shipping" value="express"> 快速配送</label><br>
  <label><input type="radio" name="shipping" value="pickup"> 門市取貨</label>
</fieldset>

<!-- 停用整個群組 -->
<fieldset disabled>
  <legend>暫時無法使用的功能</legend>
  <input type="text" name="disabled-field">
  <button type="button">按鈕</button>
</fieldset>

<!-- 巢狀 fieldset -->
<fieldset>
  <legend>帳號設定</legend>

  <fieldset>
    <legend>基本資訊</legend>
    <input type="text" name="username" placeholder="使用者名稱">
  </fieldset>

  <fieldset>
    <legend>安全性</legend>
    <input type="password" name="password" placeholder="密碼">
  </fieldset>
</fieldset>
```

### ✨ 示範效果

<fieldset>
  <legend>聯絡資訊</legend>
  <label for="demo-fieldset-name">姓名:</label>
  <input type="text" id="demo-fieldset-name"><br><br>
  <label for="demo-fieldset-email">Email:</label>
  <input type="email" id="demo-fieldset-email">
</fieldset>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

### 無障礙建議

- ✅ 使用 `<legend>` 提供群組標題
- ✅ 用於組織相關的表單欄位
- ✅ 特別適合 radio 和 checkbox 群組
- ✅ 使用 `disabled` 可一次停用所有欄位

---

## `<legend>` - 群組標題

### 說明
`<legend>` 為 `<fieldset>` 定義標題。

### 語法
```html
<fieldset>
  <legend>標題文字</legend>
</fieldset>
```

### 📌 程式碼範例

```html
<fieldset>
  <legend>付款資訊</legend>
  <label for="card-number">卡號:</label>
  <input type="text" id="card-number" name="card-number">
</fieldset>

<!-- 自訂樣式的 legend -->
<fieldset>
  <legend style="background-color: #f0f0f0; padding: 5px 10px; border-radius: 5px;">
    個人偏好設定
  </legend>
  <label><input type="checkbox" name="dark-mode"> 深色模式</label>
</fieldset>
```

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |

---

## `<datalist>` - 資料清單

### 說明
`<datalist>` 提供輸入欄位的建議選項清單，使用者可以選擇或自行輸入。

### 語法
```html
<input list="datalist-id">
<datalist id="datalist-id">
  <option value="選項1">
  <option value="選項2">
</datalist>
```

### 📌 程式碼範例

```html
<!-- 基本 datalist -->
<label for="browser">選擇瀏覽器:</label>
<input type="text" id="browser" name="browser" list="browsers">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
  <option value="Opera">
</datalist>

<!-- 網址建議 -->
<label for="website">網站:</label>
<input type="url" id="website" name="website" list="popular-sites">
<datalist id="popular-sites">
  <option value="https://www.google.com">
  <option value="https://www.github.com">
  <option value="https://www.stackoverflow.com">
</datalist>

<!-- 顏色建議 -->
<label for="color-choice">選擇顏色:</label>
<input type="color" id="color-choice" list="preset-colors">
<datalist id="preset-colors">
  <option value="#ff0000">
  <option value="#00ff00">
  <option value="#0000ff">
</datalist>
```

### ✨ 示範效果

<label for="demo-datalist">選擇程式語言 (或輸入其他):</label><br>
<input type="text" id="demo-datalist" list="demo-languages" placeholder="開始輸入...">
<datalist id="demo-languages">
  <option value="JavaScript">
  <option value="Python">
  <option value="Java">
  <option value="C++">
  <option value="Ruby">
  <option value="Go">
</datalist>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 20+ | ✅ 4+ | ✅ 12.1+ | ✅ All | ✅ 10+ |

### 無障礙建議

- ✅ 提供常用選項的建議
- ✅ 允許使用者自行輸入
- ✅ 選項要清楚明確
- ⚠️ 不是所有瀏覽器都支援所有 input type

### 使用注意事項

```html
<!-- ❌ 錯誤：list 對應錯誤的 ID -->
<input list="wrong-id">
<datalist id="correct-id">
  <option value="選項">
</datalist>

<!-- ✅ 正確：list 對應正確的 ID -->
<input list="my-list">
<datalist id="my-list">
  <option value="選項">
</datalist>
```

---

## `<output>` - 輸出結果

### 說明
`<output>` 用於顯示計算或使用者操作的結果。

### 語法
```html
<output name="名稱" for="相關欄位ID">輸出內容</output>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `for` | 相關的輸入欄位 ID | ID (空格分隔) | 否 |
| `name` | 輸出名稱 | 文字 | 否 |
| `form` | 關聯的表單 ID | ID | 否 |

### 📌 程式碼範例

```html
<!-- 計算結果 -->
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
  <input type="number" id="a" value="0"> +
  <input type="number" id="b" value="0"> =
  <output name="result" for="a b">0</output>
</form>

<!-- 滑桿當前值 -->
<form oninput="volume-output.value = volume.value">
  <label for="volume">音量:</label>
  <input type="range" id="volume" name="volume" min="0" max="100" value="50">
  <output name="volume-output" for="volume">50</output>
</form>

<!-- 百分比計算 -->
<form oninput="percent.value = Math.round((score.value / total.value) * 100) + '%'">
  得分: <input type="number" id="score" value="80" min="0" max="100">
  滿分: <input type="number" id="total" value="100" readonly>
  百分比: <output name="percent" for="score total">80%</output>
</form>
```

### ✨ 示範效果

<form oninput="demo_result.value = parseInt(demo_a.value) + parseInt(demo_b.value)">
  <input type="number" id="demo_a" value="5" style="width: 60px;"> +
  <input type="number" id="demo_b" value="3" style="width: 60px;"> =
  <output name="demo_result" for="demo_a demo_b" style="font-weight: bold;">8</output>
</form>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 10+ | ✅ 4+ | ✅ 7+ | ✅ All | ❌ |

---

## `<progress>` - 進度條

### 說明
`<progress>` 顯示任務的完成進度。

### 語法
```html
<progress value="當前值" max="最大值">備援文字</progress>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `value` | 當前進度值 | 數字 | 否 |
| `max` | 最大值 | 數字 | 否 (預設 1.0) |

### 📌 程式碼範例

```html
<!-- 基本進度條 -->
<label for="file-progress">檔案下載進度:</label>
<progress id="file-progress" value="70" max="100">70%</progress>

<!-- 不確定的進度 (沒有 value) -->
<progress>載入中...</progress>

<!-- 百分比進度 -->
<label>完成度: <span id="percent">0%</span></label><br>
<progress id="upload" value="0" max="100"></progress>
<script>
  let progress = 0;
  const interval = setInterval(() => {
    progress += 10;
    document.getElementById('upload').value = progress;
    document.getElementById('percent').textContent = progress + '%';
    if (progress >= 100) clearInterval(interval);
  }, 500);
</script>

<!-- 自訂樣式 -->
<progress value="60" max="100" style="width: 100%; height: 30px;"></progress>
```

### ✨ 示範效果

<label>下載進度:</label><br>
<progress value="45" max="100"></progress> 45%

<br><br>

<label>處理中:</label><br>
<progress></progress>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 8+ | ✅ 6+ | ✅ 6+ | ✅ All | ✅ 10+ |

### 無障礙建議

- ✅ 提供文字說明進度
- ✅ 使用 `<label>` 關聯
- ✅ 在標籤內提供備援文字
- ✅ 更新進度時同步更新說明文字

---

## `<meter>` - 測量儀表

### 說明
`<meter>` 顯示已知範圍內的標量測量值，如磁碟使用量、投票結果等。

### 語法
```html
<meter value="當前值" min="最小值" max="最大值">備援文字</meter>
```

### 常用屬性

| 屬性 | 說明 | 值 | 必需 |
|------|------|-----|------|
| `value` | 當前值 | 數字 | 是 |
| `min` | 最小值 | 數字 | 否 (預設 0) |
| `max` | 最大值 | 數字 | 否 (預設 1) |
| `low` | 低值臨界點 | 數字 | 否 |
| `high` | 高值臨界點 | 數字 | 否 |
| `optimum` | 最佳值 | 數字 | 否 |

### 📌 程式碼範例

```html
<!-- 基本 meter -->
<label for="disk-usage">磁碟使用量:</label>
<meter id="disk-usage" value="60" min="0" max="100">60%</meter>

<!-- 有臨界值的 meter -->
<label for="battery">電池電量:</label>
<meter id="battery" value="80" min="0" max="100"
       low="20" high="80" optimum="100">80%</meter>

<!-- 不同狀態範例 -->
<p>低電量 (紅色):</p>
<meter value="15" min="0" max="100" low="20" high="80" optimum="100"></meter>

<p>中等電量 (黃色):</p>
<meter value="50" min="0" max="100" low="20" high="80" optimum="100"></meter>

<p>充足電量 (綠色):</p>
<meter value="90" min="0" max="100" low="20" high="80" optimum="100"></meter>

<!-- 投票結果 -->
<p>支持度: 65%</p>
<meter value="65" min="0" max="100" optimum="100"></meter>
```

### ✨ 示範效果

<label>CPU 使用率:</label><br>
<meter value="45" min="0" max="100" low="30" high="70" optimum="50">45%</meter>

<br><br>

<label>記憶體使用 (警告):</label><br>
<meter value="85" min="0" max="100" low="30" high="70" optimum="30">85%</meter>

### 瀏覽器支援

| Chrome | Firefox | Safari | Edge | IE |
|--------|---------|--------|------|-----|
| ✅ 8+ | ✅ 6+ | ✅ 6+ | ✅ All | ❌ |

### 無障礙建議

- ✅ 提供文字說明測量值
- ✅ 使用 `<label>` 關聯
- ✅ 在標籤內提供備援文字
- ⚠️ 不要用於進度指示（使用 `<progress>`）

### 使用注意事項

```html
<!-- ❌ 錯誤：用 meter 顯示進度 -->
<meter value="30" max="100">下載進度 30%</meter>

<!-- ✅ 正確：用 progress 顯示進度 -->
<progress value="30" max="100">下載進度 30%</progress>

<!-- ✅ 正確：用 meter 顯示測量值 -->
<meter value="8" min="0" max="10">評分 8/10</meter>
```

---

## 實際應用範例

### 登入表單

```html
<form action="/login" method="POST" autocomplete="on">
  <h2>會員登入</h2>

  <div>
    <label for="login-email">電子郵件:</label>
    <input type="email" id="login-email" name="email"
           placeholder="example@mail.com" required autofocus>
  </div>

  <div>
    <label for="login-password">密碼:</label>
    <input type="password" id="login-password" name="password"
           minlength="8" required>
  </div>

  <div>
    <label>
      <input type="checkbox" name="remember" value="yes">
      記住我
    </label>
  </div>

  <div>
    <button type="submit">登入</button>
    <button type="button" onclick="location.href='/forgot-password'">忘記密碼?</button>
  </div>
</form>
```

#### ✨ 示範效果

<form style="border: 1px solid #ccc; padding: 20px; max-width: 400px;">
  <h3>會員登入</h3>

  <label for="demo-login-email">電子郵件:</label><br>
  <input type="email" id="demo-login-email" placeholder="example@mail.com"
         style="width: 100%; padding: 8px; margin-bottom: 10px;" required>

  <label for="demo-login-password">密碼:</label><br>
  <input type="password" id="demo-login-password"
         style="width: 100%; padding: 8px; margin-bottom: 10px;" required>

  <label style="display: block; margin-bottom: 15px;">
    <input type="checkbox"> 記住我
  </label>

  <button type="submit" style="padding: 10px 20px; margin-right: 10px;">登入</button>
  <button type="button" style="padding: 10px 20px;">忘記密碼?</button>
</form>

---

### 註冊表單

```html
<form action="/register" method="POST">
  <h2>新會員註冊</h2>

  <fieldset>
    <legend>基本資料</legend>

    <div>
      <label for="reg-username">使用者名稱 <span style="color: red;">*</span></label>
      <input type="text" id="reg-username" name="username"
             pattern="[A-Za-z0-9_]{4,20}"
             title="4-20 個字元，只能包含字母、數字和底線"
             required>
    </div>

    <div>
      <label for="reg-email">電子郵件 <span style="color: red;">*</span></label>
      <input type="email" id="reg-email" name="email" required>
    </div>

    <div>
      <label for="reg-password">密碼 <span style="color: red;">*</span></label>
      <input type="password" id="reg-password" name="password"
             pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}"
             title="至少 8 個字元，包含大小寫字母和數字"
             required>
    </div>

    <div>
      <label for="reg-confirm">確認密碼 <span style="color: red;">*</span></label>
      <input type="password" id="reg-confirm" name="confirm-password" required>
    </div>
  </fieldset>

  <fieldset>
    <legend>個人資訊</legend>

    <div>
      <label for="reg-name">真實姓名:</label>
      <input type="text" id="reg-name" name="full-name">
    </div>

    <div>
      <label for="reg-birthday">生日:</label>
      <input type="date" id="reg-birthday" name="birthday"
             max="2008-01-02">
    </div>

    <div>
      <label>性別:</label><br>
      <label><input type="radio" name="gender" value="male"> 男性</label>
      <label><input type="radio" name="gender" value="female"> 女性</label>
      <label><input type="radio" name="gender" value="other"> 其他</label>
      <label><input type="radio" name="gender" value="prefer-not-to-say" checked> 不透露</label>
    </div>

    <div>
      <label for="reg-country">國家:</label>
      <select id="reg-country" name="country">
        <option value="">請選擇</option>
        <option value="TW" selected>台灣</option>
        <option value="JP">日本</option>
        <option value="US">美國</option>
        <option value="UK">英國</option>
      </select>
    </div>
  </fieldset>

  <fieldset>
    <legend>興趣（可複選）</legend>
    <label><input type="checkbox" name="interests" value="tech"> 科技</label>
    <label><input type="checkbox" name="interests" value="sports"> 運動</label>
    <label><input type="checkbox" name="interests" value="music"> 音樂</label>
    <label><input type="checkbox" name="interests" value="travel"> 旅遊</label>
    <label><input type="checkbox" name="interests" value="food"> 美食</label>
  </fieldset>

  <div>
    <label>
      <input type="checkbox" name="agree" value="yes" required>
      我同意<a href="/terms">服務條款</a>和<a href="/privacy">隱私政策</a> <span style="color: red;">*</span>
    </label>
  </div>

  <div>
    <button type="submit">註冊</button>
    <button type="reset">清除</button>
  </div>
</form>
```

---

### 聯絡表單

```html
<form action="/contact" method="POST">
  <h2>聯絡我們</h2>

  <div>
    <label for="contact-name">您的姓名 <span style="color: red;">*</span></label>
    <input type="text" id="contact-name" name="name" required>
  </div>

  <div>
    <label for="contact-email">電子郵件 <span style="color: red;">*</span></label>
    <input type="email" id="contact-email" name="email" required>
  </div>

  <div>
    <label for="contact-phone">聯絡電話:</label>
    <input type="tel" id="contact-phone" name="phone"
           pattern="09\d{8}" placeholder="0912345678">
  </div>

  <div>
    <label for="contact-subject">主旨 <span style="color: red;">*</span></label>
    <select id="contact-subject" name="subject" required>
      <option value="">請選擇</option>
      <option value="general">一般詢問</option>
      <option value="support">技術支援</option>
      <option value="sales">業務洽詢</option>
      <option value="complaint">客訴</option>
      <option value="other">其他</option>
    </select>
  </div>

  <div>
    <label for="contact-message">訊息內容 <span style="color: red;">*</span></label>
    <textarea id="contact-message" name="message" rows="6"
              minlength="10" maxlength="1000"
              placeholder="請詳細描述您的問題或需求..."
              required></textarea>
    <small>字數限制: 10-1000 字</small>
  </div>

  <div>
    <label for="contact-file">附件（選填）:</label>
    <input type="file" id="contact-file" name="attachment"
           accept=".pdf,.doc,.docx,.jpg,.png" multiple>
    <small>可上傳 PDF、Word 文件或圖片，最多 5 個檔案</small>
  </div>

  <div>
    <label for="contact-rating">滿意度評分:</label>
    <input type="range" id="contact-rating" name="rating"
           min="1" max="5" value="5"
           oninput="document.getElementById('rating-value').textContent = this.value">
    <output id="rating-value">5</output> / 5
  </div>

  <div>
    <button type="submit">送出</button>
    <button type="reset">重新填寫</button>
  </div>
</form>
```

---

### 搜尋表單

```html
<!-- 簡單搜尋 -->
<form action="/search" method="GET">
  <label for="simple-search">搜尋:</label>
  <input type="search" id="simple-search" name="q"
         placeholder="輸入關鍵字..." required>
  <button type="submit">搜尋</button>
</form>

<!-- 進階搜尋 -->
<form action="/advanced-search" method="GET">
  <h3>進階搜尋</h3>

  <div>
    <label for="adv-keyword">關鍵字:</label>
    <input type="search" id="adv-keyword" name="keyword"
           list="search-suggestions">
    <datalist id="search-suggestions">
      <option value="HTML">
      <option value="CSS">
      <option value="JavaScript">
      <option value="Python">
    </datalist>
  </div>

  <div>
    <label for="adv-category">分類:</label>
    <select id="adv-category" name="category">
      <option value="">所有分類</option>
      <option value="tech">科技</option>
      <option value="business">商業</option>
      <option value="entertainment">娛樂</option>
      <option value="sports">運動</option>
    </select>
  </div>

  <div>
    <label for="adv-date-from">日期從:</label>
    <input type="date" id="adv-date-from" name="date-from">

    <label for="adv-date-to">到:</label>
    <input type="date" id="adv-date-to" name="date-to">
  </div>

  <div>
    <label>排序方式:</label><br>
    <label><input type="radio" name="sort" value="relevance" checked> 相關性</label>
    <label><input type="radio" name="sort" value="date"> 日期</label>
    <label><input type="radio" name="sort" value="popularity"> 熱門度</label>
  </div>

  <div>
    <button type="submit">搜尋</button>
    <button type="reset">清除</button>
  </div>
</form>
```

---

### 訂單表單

```html
<form action="/checkout" method="POST">
  <h2>結帳</h2>

  <fieldset>
    <legend>收件資訊</legend>

    <div>
      <label for="order-name">收件人姓名 <span style="color: red;">*</span></label>
      <input type="text" id="order-name" name="recipient-name" required>
    </div>

    <div>
      <label for="order-phone">聯絡電話 <span style="color: red;">*</span></label>
      <input type="tel" id="order-phone" name="phone"
             pattern="09\d{8}" required>
    </div>

    <div>
      <label for="order-email">電子郵件 <span style="color: red;">*</span></label>
      <input type="email" id="order-email" name="email" required>
    </div>

    <div>
      <label for="order-address">收件地址 <span style="color: red;">*</span></label>
      <textarea id="order-address" name="address" rows="3" required></textarea>
    </div>
  </fieldset>

  <fieldset>
    <legend>配送方式</legend>
    <label>
      <input type="radio" name="shipping-method" value="home" checked>
      宅配到府 (+$0)
    </label><br>
    <label>
      <input type="radio" name="shipping-method" value="store">
      超商取貨 (+$60)
    </label><br>
    <label>
      <input type="radio" name="shipping-method" value="express">
      快速配送 (+$150)
    </label>
  </fieldset>

  <fieldset>
    <legend>付款方式</legend>
    <label>
      <input type="radio" name="payment-method" value="credit" checked>
      信用卡
    </label><br>
    <label>
      <input type="radio" name="payment-method" value="atm">
      ATM 轉帳
    </label><br>
    <label>
      <input type="radio" name="payment-method" value="cod">
      貨到付款
    </label>
  </fieldset>

  <div id="credit-card-info">
    <fieldset>
      <legend>信用卡資訊</legend>

      <div>
        <label for="card-number">卡號 <span style="color: red;">*</span></label>
        <input type="text" id="card-number" name="card-number"
               pattern="\d{16}" placeholder="1234567890123456"
               maxlength="16">
      </div>

      <div>
        <label for="card-name">持卡人姓名 <span style="color: red;">*</span></label>
        <input type="text" id="card-name" name="card-name">
      </div>

      <div>
        <label for="card-expiry">有效期限 <span style="color: red;">*</span></label>
        <input type="month" id="card-expiry" name="card-expiry"
               min="2026-01">
      </div>

      <div>
        <label for="card-cvv">安全碼 (CVV) <span style="color: red;">*</span></label>
        <input type="text" id="card-cvv" name="card-cvv"
               pattern="\d{3}" maxlength="3" placeholder="123">
      </div>
    </fieldset>
  </div>

  <div>
    <label for="order-note">訂單備註:</label>
    <textarea id="order-note" name="note" rows="3"
              placeholder="有任何特殊需求請在此說明..."></textarea>
  </div>

  <div>
    <label>
      <input type="checkbox" name="invoice" value="yes">
      需要發票
    </label>
  </div>

  <div>
    <h3>訂單總計: $1,250</h3>
    <button type="submit">確認送出訂單</button>
    <button type="button" onclick="history.back()">返回購物車</button>
  </div>
</form>
```

---

## 表單驗證

### HTML5 內建驗證屬性

HTML5 提供多種驗證屬性，無需 JavaScript 即可進行基本驗證：

| 驗證屬性 | 說明 | 範例 |
|---------|------|------|
| `required` | 必填欄位 | `<input type="text" required>` |
| `pattern` | 正規表達式驗證 | `<input type="text" pattern="[A-Za-z]{3}">` |
| `minlength` | 最小字元長度 | `<input type="text" minlength="8">` |
| `maxlength` | 最大字元長度 | `<input type="text" maxlength="20">` |
| `min` | 最小值 | `<input type="number" min="0">` |
| `max` | 最大值 | `<input type="number" max="100">` |
| `step` | 數值間隔 | `<input type="number" step="5">` |
| `type` | 特定格式驗證 | `<input type="email">`, `<input type="url">` |

### 📌 驗證範例

```html
<form>
  <!-- 必填驗證 -->
  <label for="val-required">必填欄位:</label>
  <input type="text" id="val-required" required>

  <!-- Email 格式驗證 -->
  <label for="val-email">Email:</label>
  <input type="email" id="val-email" required>

  <!-- 數字範圍驗證 -->
  <label for="val-age">年齡 (18-120):</label>
  <input type="number" id="val-age" min="18" max="120" required>

  <!-- 字串長度驗證 -->
  <label for="val-username">使用者名稱 (4-20 字元):</label>
  <input type="text" id="val-username" minlength="4" maxlength="20" required>

  <!-- 正規表達式驗證 -->
  <label for="val-phone">手機號碼 (格式: 0912345678):</label>
  <input type="tel" id="val-phone" pattern="09\d{8}"
         title="請輸入正確的台灣手機號碼格式" required>

  <!-- 自訂錯誤訊息 (使用 title) -->
  <label for="val-password">密碼:</label>
  <input type="password" id="val-password"
         pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}"
         title="密碼必須至少 8 個字元，包含大小寫字母和數字" required>

  <button type="submit">提交</button>
</form>
```

### CSS 驗證狀態樣式

```html
<style>
/* 必填欄位標記 */
input:required {
  border-left: 3px solid #ff6b6b;
}

/* 有效輸入 */
input:valid {
  border-color: #51cf66;
}

/* 無效輸入 */
input:invalid {
  border-color: #ff6b6b;
}

/* 聚焦時的無效輸入 */
input:invalid:focus {
  outline: 2px solid #ff6b6b;
}

/* 停用欄位 */
input:disabled {
  background-color: #f1f3f5;
  cursor: not-allowed;
}
</style>

<form>
  <label for="styled-email">Email:</label>
  <input type="email" id="styled-email" required>

  <label for="styled-age">年齡:</label>
  <input type="number" id="styled-age" min="0" max="120" required>

  <button type="submit">提交</button>
</form>
```

### 停用表單驗證

```html
<!-- 停用整個表單的驗證 -->
<form novalidate>
  <input type="email" required>
  <button type="submit">提交</button>
</form>

<!-- 特定按鈕不驗證 -->
<form>
  <input type="email" required>
  <button type="submit">提交 (會驗證)</button>
  <button type="submit" formnovalidate>儲存草稿 (不驗證)</button>
</form>
```

---

## 最佳實踐總結

### ✅ 必須做的事

1. **使用語意化標籤**
   - 使用正確的 input type
   - 使用 `<label>` 關聯表單欄位
   - 使用 `<fieldset>` 組織相關欄位

2. **提升使用者體驗**
   - 提供清楚的 `placeholder` 提示
   - 使用 `autofocus` 在適當欄位
   - 提供即時的表單驗證回饋
   - 使用 `autocomplete` 屬性

3. **無障礙設計**
   - 每個輸入欄位都要有 `<label>`
   - 使用 `required` 和視覺標記 (如 `*`) 標示必填欄位
   - 提供明確的錯誤訊息
   - 使用適當的 `title` 屬性說明驗證規則

4. **表單驗證**
   - 使用 HTML5 內建驗證屬性
   - 提供清楚的驗證規則說明
   - 前端和後端都要驗證

5. **安全性**
   - 敏感資料使用 `type="password"`
   - 使用 HTTPS 傳輸表單資料
   - 實作 CSRF 防護
   - 檔案上傳要限制類型和大小

### ❌ 避免的事

1. **不良的使用者體驗**
   - ❌ 不要省略 `<label>` 標籤
   - ❌ 不要過度使用 `required`
   - ❌ 不要在沒有說明的情況下使用複雜的 `pattern`
   - ❌ 不要使用 `placeholder` 取代 `<label>`

2. **錯誤的語意**
   - ❌ 不要用錯誤的 input type (如用 text 取代 email)
   - ❌ 不要巢狀 `<form>` 元素
   - ❌ 不要混淆 `<button>` 和 `<input type="button">` 的用途

3. **無障礙問題**
   - ❌ 不要只用顏色區分狀態
   - ❌ 不要省略 `alt` 屬性 (在 type="image" 時)
   - ❌ 不要使用過小的可點擊區域

4. **安全性問題**
   - ❌ 不要只依賴前端驗證
   - ❌ 不要在 URL 中傳遞敏感資訊 (使用 POST)
   - ❌ 不要儲存明文密碼

### 🎯 進階優化

1. **效能優化**
   - 使用 `autocomplete` 減少輸入時間
   - 大型表單考慮分頁或步驟式設計
   - 使用 `datalist` 提供建議選項

2. **進階驗證**
   - 結合 JavaScript 提供即時驗證
   - 使用 Constraint Validation API
   - 實作自訂驗證邏輯

3. **響應式設計**
   - 在行動裝置上使用適當的 input type
   - 調整表單欄位大小適應螢幕
   - 確保按鈕足夠大方便點擊

4. **進階功能**
   - 實作自動儲存草稿
   - 提供表單填寫進度指示
   - 使用 `<output>` 顯示即時計算結果

---

[⬆️ 回到頂部](#表單標籤-forms) | [📑 回索引頁](index.md)
