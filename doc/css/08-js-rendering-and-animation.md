# 08. JS 渲染機制與動畫原理 (Rendering Engine & Event Loop)

這份文件解釋為什麼在 JavaScript 中修改 DOM 不會立即反映在螢幕上，以及如何利用這個特性來做高效能動畫。

## 1. 為什麼畫面不會閃爍？(The "No-Flash" Mystery)

你在實戰中遇到的狀況流程如下：

1.  **Write**: 寫入資料 (DOM 變更)。
2.  **Read**: 讀取 `scrollHeight` (瀏覽器為了給你正確數值，被迫執行一次 **Layout** 計算)。
3.  **Write**: 設定 `height: 0`。
4.  **Write**: 設定 `height: target`。
5.  **End**: JS 執行結束。

### 關鍵原因：Layout 是同步的，Paint 是非同步的

瀏覽器的渲染管線 (Rendering Pipeline) 大致如下：

> **JavaScript** -> **Style** -> **Layout (排版)** -> **Paint (繪製)** -> **Composite (合成)**

*   當你呼叫 `element.scrollHeight` 時，瀏覽器觸發了 **同步 Layout (Synchronous Layout)**。它必須在記憶體中算出位置，才能回傳數值給你。**但這時候它還不會把結果畫到螢幕上！**
*   螢幕的更新 (Paint) 通常發生在 **JavaScript Task 結束後**，或是下一幀 (Next Frame) 之前。
*   因為你的程式碼是連續執行的，當瀏覽器準備要 Paint 的時候，你的高度已經被改回 0 (或目標高度) 了。中間那個「全開」的狀態只存在於運算過程中，從未上色。

## 2. 強制重排 (Forced Synchronous Layout)

雖然「不閃爍」是好事，但要注意效能。當你在同一個 Frame 裡「先寫 DOM，再讀取 Layout 屬性」時，會強迫瀏覽器中斷當前工作去計算排版。

**會觸發強制重排的屬性 (讀取時)：**
- `offsetTop`, `offsetLeft`, `offsetWidth`, `offsetHeight`
- `scrollTop`, `scrollLeft`, `scrollWidth`, `scrollHeight`
- `getComputedStyle()`

如果在迴圈中頻繁做這種操作，會導致 **Layout Thrashing (佈局抖動)**，嚴重影響效能。

---

## 3. 實戰：Height 0 to Auto 動畫

CSS `transition` 不支援 `height: auto`。我們必須算出具體的 px 值才能做動畫。

### 標準作法 (FLIP 概念變體)

```javascript
const el = document.querySelector('.box');

// 1. 放入內容
el.innerHTML = "...大量的內容...";

// 2. 獲取真實高度 (這行會觸發 Layout，但不會 Paint)
const targetHeight = el.scrollHeight;

// 3. 設定初始狀態 (Start)
el.style.height = '0px';
el.style.transition = 'height 0.3s ease';

// 4. 【關鍵】強制瀏覽器套用初始狀態 (Force Reflow)
// 如果不加這一行，瀏覽器會把 0px 和 targetHeight 合併處理，導致動畫失效 (直接跳到結果)
el.offsetHeight; 

// 5. 設定結束狀態 (End)
// 使用 requestAnimationFrame 確保在下一幀執行，效果更穩
requestAnimationFrame(() => {
  el.style.height = targetHeight + 'px';
});
```

### 為什麼需要 `el.offsetHeight` 或 `requestAnimationFrame`？

如果你寫：
```javascript
el.style.height = '0px';
el.style.height = '100px';
```
瀏覽器會進行「批次優化 (Batching)」，它會認為你最後只想要 100px，所以直接渲染 100px，不會有動畫。

你需要透過讀取 `offsetHeight` 來打斷批次優化，告訴瀏覽器：「現在！立刻！確認 0px 的狀態！」，然後再設定 100px，這樣瀏覽器才知道要從 0 變到 100。

---

## 4. 瀏覽器渲染時序圖

```text
[JS Start]
  |
  |-- 修改 DOM (加入內容)
  |-- 讀取 scrollHeight -> [觸發 Layout 計算] (使用者看不到)
  |-- 設定 height = 0
  |-- 讀取 offsetHeight -> [觸發 Layout 計算] (確認 0 的狀態)
  |-- 設定 height = 100px
  |
[JS End]
  |
[Browser Paint] -> 使用者終於看到畫面 (此時高度已經在跑動畫了)
```
