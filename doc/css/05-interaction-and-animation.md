# 05. 動畫與交互 (Animation & Interaction)

## 1. 變形 (Transforms)

`transform` 屬性用於改變元素的形狀、大小和位置。它**不會**影響周圍元素的佈局 (reflow)，效能較好。

- **`translate(x, y)`**: 位移 (如 `translate(10px, 50%)`)。
- **`scale(x, y)`**: 縮放 (如 `scale(1.2)` 放大 20%)。
- **`rotate(angle)`**: 旋轉 (如 `rotate(45deg)`).
- **`skew(x, y)`**: 傾斜。
- **`transform-origin`**: 變形的原點 (預設 center)。

## 2. 過渡 (Transitions)

`transition` 用於在狀態改變 (如 `:hover`) 時建立平滑效果。

- **`transition-property`**: 要過渡的屬性 (如 `opacity`, `transform`, `all`).
- **`transition-duration`**: 持續時間 (如 `0.3s`).
- **`transition-timing-function`**: 速度曲線。
    - `ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier(...)`.
- **`transition-delay`**: 延遲開始時間。

**簡寫範例:**
```css
.btn {
  transition: all 0.3s ease-in-out;
}
```

## 3. 關鍵影格動畫 (Keyframe Animations)

比 Transition 更複雜，可自動運行或循環。

### 定義動畫
```css
@keyframes slideIn {
  from {
    transform: translateX(-100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}
```

### 使用動畫
- **`animation-name`**: 對應 @keyframes 名稱。
- **`animation-duration`**: 持續時間。
- **`animation-timing-function`**: 速度曲線。
- **`animation-delay`**: 延遲。
- **`animation-iteration-count`**: 播放次數 (`infinite` 為無限).
- **`animation-direction`**: 方向 (`normal`, `reverse`, `alternate` 來回播放).
- **`animation-fill-mode`**: 動畫結束後的狀態 (`forwards` 停在最後一格).

**簡寫範例:**
```css
.element {
  animation: slideIn 1s ease forwards;
}
```

## 4. 交互與游標 (Interaction)

- **`cursor`**: 滑鼠游標樣式。
    - `pointer` (手形，用於連結/按鈕), `default`, `text`, `not-allowed`, `grab`.
- **`pointer-events`**: 控制元素是否能被點擊。
    - `none`: 穿透元素 (點擊不到)。
    - `auto`: 恢復預設。
- **`user-select`**: 控制文字是否可被選取。
    - `none`: 禁止選取文字。
