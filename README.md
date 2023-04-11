# falra_progress_bar
## Falra 銀河白洞進度條

一個使用 Vanta.js 實現的炫爆進度條。

## 使用方式

1. 下載或 clone 此專案。
2. 在你的 HTML 文件中引入 `vanta.halo.min.js` 和 `falra-progress-bar.js`。
3. 在你的 HTML 文件中添加一個空的 `<div>` 元素，並賦予它一個 id，例如 `vanta-bg`。
4. 在你的 HTML 文件中添加一個用於顯示進度的元素，例如 `progress-text`。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Falra 進度條</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    #vanta-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    #progress-text {
      position: fixed;
      top: 20px;
      left: 20px;
      color: #f0f0f0;
      font-size: 24px;
      z-index: 10;
    }
  </style>
</head>
<body>
  <div id="vanta-bg"></div>
  <div id="progress-text">0%</div>

  <!-- Vanta.js 依賴 -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r110/three.min.js"></script>

  <!-- Vanta.js 库 -->
  <script src="vanta.halo.min.js"></script>
  <script src="falra-progress-bar.js"></script>

</body>
</html>
```

## 自定義

你可以自定義進度條的顏色、大小、位置等屬性。

在 `falra-progress-bar.js` 文件中，可以通過修改以下屬性來達到自定義效果：

```javascript
const vantaEffect = VANTA.HALO({
  el: "#vanta-bg",
  backgroundColor: 0x202428,  // 背景顏色
  size: 0.1,  // 大小
  xOffset: 0.16,  // X 軸偏移量
  yOffset: -0.02,  // Y 軸偏移量
  zOffset: 0.19  // Z 軸偏移量
});
```

同時，你可以在 `updateProgress` 函数中修改進度條的變化方式，例如修改大小和偏移量等：

```javascript
const updateProgress = () => {
  progress += 1;
  if (progress <= 100) {
    progressText.textContent = progress + '%';

    // 更新大小
    const newSize = 0.1 + (2.9 - 0.1) * (progress / 100);
    vantaEffect.setOptions({ size: newSize });

    // 更新 Y 軸偏移量
    const newYOffset = -0.02 + (0 - (-0.02)) * (progress / 100);
    vantaEffect.setOptions({ yOffset: newYOffset });

    setTimeout(updateProgress, 1000);
  }
};
```
