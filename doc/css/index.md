# W3C CSS 標準規範指南 (CSS Standards Guide)

這份文件彙整了基於 W3C 規範的 CSS 規則與語法，旨在提供一個結構化的參考指南。

## 📚 目錄 (Table of Contents)

### 1. 核心基礎
- **[01-selectors-and-cascade.md](./01-selectors-and-cascade.md)**
    - CSS 語法基礎
    - 選擇器 (Selectors) 列表
    - 優先權重 (Specificity)
    - 繼承 (Inheritance) 與 級聯 (Cascade)

### 2. 佈局系統
- **[02-box-model-and-flow.md](./02-box-model-and-flow.md)**
    - 盒模型 (Box Model): Margin, Border, Padding, Content
    - 顯示模式 (Display)
    - 定位 (Positioning)
    - 浮動 (Floats) 與 清除 (Clear)
- **[03-modern-layout.md](./03-modern-layout.md)**
    - Flexbox 彈性盒佈局
    - CSS Grid 網格佈局
    - 對齊控制 (Box Alignment)

### 3. 視覺與排版
- **[04-typography-and-decoration.md](./04-typography-and-decoration.md)**
    - 字體 (Fonts) 與 文本 (Text)
    - 顏色 (Colors) 與 透明度
    - 背景 (Backgrounds) 與 漸層 (Gradients)
    - 邊框 (Borders) 與 圓角 (Border-radius)
    - 陰影 (Shadows)

### 4. 動畫與交互
- **[05-interaction-and-animation.md](./05-interaction-and-animation.md)**
    - 變形 (Transforms)
    - 過渡 (Transitions)
    - 動畫 (Animations)
    - 偽類交互狀態 (Hover, Focus, etc.)

### 5. 響應式與邏輯
- **[06-responsive-and-variables.md](./06-responsive-and-variables.md)**
    - 媒體查詢 (Media Queries)
    - CSS 變數 (Custom Properties)
    - 數學函數 (calc, min, max, clamp)

### 6. 進階實戰與陷阱
- **[07-advanced-patterns-and-pitfalls.md](./07-advanced-patterns-and-pitfalls.md)**
    - 父層選取器 `:has()` 實戰
    - Checkbox Hack (無 JS 互動)
    - 權重與繼承的常見地雷
    - **[實體範例頁面 (Interactive Demo)](./demo.html)**：包含 Floating Label、滾動動畫等實作效果。

### 7. JS 渲染機制 (Browser Rendering)
- **[08-js-rendering-and-animation.md](./08-js-rendering-and-animation.md)**
    - 為什麼 DOM 修改不會立即閃爍 (Layout vs Paint)
    - 強制重排 (Forced Reflow)
    - 實作 `height: 0` 到 `height: auto` 動畫

### 8. 前沿技術 (Bleeding Edge)
- **[09-bleeding-edge-css.md](./09-bleeding-edge-css.md)**
    - `@property` 自定義變數類型 (讓漸層動起來)
    - `anchor()` 原生錨點定位
    - View Transitions API

### 9. 架構與工程化 (Architecture)
- **[10-architecture-and-best-practices.md](./10-architecture-and-best-practices.md)**
    - BEM 命名規範
    - CSS 變數主題策略 (Dark Mode)
    - 無障礙設計 (A11y)

---

## 參考資源 (References)

- [W3C CSS Specifications](https://www.w3.org/Style/CSS/specs.en.html)
- [MDN Web Docs - CSS](https://developer.mozilla.org/zh-TW/docs/Web/CSS)
