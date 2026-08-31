---
title: "CanvasRenderingContext2D: reset() method"
short-title: reset()
slug: Web/API/CanvasRenderingContext2D/reset
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.reset
---

{{APIRef("Canvas API")}}

**`CanvasRenderingContext2D.reset()`** 方法用于将 2D 渲染上下文重置为其默认状态，从而无需显式重置所有属性即可重新用于绘制其他内容。

重置操作会清除后备缓冲区、绘图状态栈、所有已定义的路径以及样式。这包括当前的[变换](/en-US/docs/Web/API/CanvasRenderingContext2D#transformations)矩阵、[合成](/en-US/docs/Web/API/CanvasRenderingContext2D#compositing)属性、裁剪区域、虚线列表、[线条样式](/en-US/docs/Web/API/CanvasRenderingContext2D#line_styles)、[文本样式](/en-US/docs/Web/API/CanvasRenderingContext2D#text_styles)、[阴影](/en-US/docs/Web/API/CanvasRenderingContext2D#shadows)、[图像平滑](/en-US/docs/Web/API/CanvasRenderingContext2D#image_smoothing)、[滤镜](/en-US/docs/Web/API/CanvasRenderingContext2D#filters)等等。

## 语法

```js-nolint
reset()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

此示例展示了如何在重绘之前使用 `reset()` 完全清除上下文。

首先我们定义一个按钮和一个画布。

```css
#toggle-reset {
  display: block;
}
```

```html
<button id="toggle-reset">Toggle</button>
<canvas id="my-house" width="500" height="200"></canvas>
```

代码首先获取画布的 `2d` 上下文。然后定义函数分别使用该上下文绘制矩形和圆形。

```js
// 获取 2d 上下文
const canvas = document.getElementById("my-house");
const ctx = canvas.getContext("2d");

function drawRect() {
  // 设置线宽
  ctx.lineWidth = 10;

  // 描边矩形轮廓
  ctx.strokeRect(50, 50, 150, 100);

  // 创建填充文本
  ctx.font = "50px serif";
  ctx.fillText("Rect!", 70, 110);
}

function drawCircle() {
  // 设置线宽
  ctx.lineWidth = 5;

  // 描边圆形
  ctx.beginPath();
  ctx.arc(300, 100, 50, 0, 2 * Math.PI);
  ctx.stroke();

  // 创建填充文本
  ctx.font = "25px sans-serif";
  ctx.fillText("Circle!", 265, 100);
}
```

然后我们使用其函数绘制矩形。按钮用于在圆形和矩形之间切换。注意在绘制之前调用了 `reset()` 来清除上下文。

```js
drawRect();

// 使用按钮在圆形和矩形之间切换
let toggle = true;
const myButton = document.getElementById("toggle-reset");

myButton.addEventListener("click", () => {
  ctx.reset(); // 清除上下文！
  if (toggle) {
    drawCircle();
  } else {
    drawRect();
  }
  toggle = !toggle;
});
```

结果如下所示：

{{EmbedLiveSample("Examples", 500, 250)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 定义此方法的接口：{{domxref("CanvasRenderingContext2D")}}
