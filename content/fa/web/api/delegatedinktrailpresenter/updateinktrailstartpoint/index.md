---
title: "DelegatedInkTrailPresenter: updateInkTrailStartPoint() method"
short-title: updateInkTrailStartPoint()
slug: Web/API/DelegatedInkTrailPresenter/updateInkTrailStartPoint
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.DelegatedInkTrailPresenter.updateInkTrailStartPoint
---

{{APIRef("Ink API")}}{{SeeCompatTable}}

**`updateInkTrailStartPoint()`** 方法属于 {{domxref("DelegatedInkTrailPresenter")}} 接口，用于指明哪个 {{domxref("PointerEvent")}} 被用作当前帧的最后渲染点，从而允许操作系统级别的合成器在下一次指针事件派发之前，渲染一段委派（delegated）的墨迹轨迹（ink trail）。

## 语法

```js-nolint
updateInkTrailStartPoint(event, style)
```

### 参数

- `event` {{optional_inline}}
  - : 一个 {{domxref("PointerEvent")}}。
- `style`
  - : 一个定义轨迹样式的对象，包含以下属性：
    - `color`
      - : 一个 {{jsxref("String")}}，包含有效的 CSS 颜色代码，表示呈现器在渲染墨迹轨迹时使用的颜色。
    - `diameter`
      - : 一个数字，表示呈现器在渲染墨迹轨迹时使用的直径。

### 返回值

`undefined`。

### 异常

- `Error` {{domxref("DOMException")}}
  - : 在以下情况下会抛出错误并中止操作：
    - `color` 属性不包含有效的 CSS 颜色代码。
    - `diameter` 属性不是数字或小于 1。
    - {{domxref("DelegatedInkTrailPresenter.presentationArea", "presentationArea")}} 元素在渲染之前或渲染期间被从文档中移除。

## 示例

### 绘制墨迹轨迹

在此示例中，我们在一个 2D 画布上绘制轨迹。在代码开头，我们调用 {{domxref("Ink.requestPresenter()")}}，将画布作为呈现区域交由它处理，并将返回的 promise 存储在 `presenter` 变量中。

随后，在 `pointermove` 事件监听器中，每次事件触发时，轨迹起点的新位置都会被绘制到画布上。此外，当 `presenter` promise 兑现时返回的 {{domxref("DelegatedInkTrailPresenter")}} 对象会调用其 `updateInkTrailStartPoint()` 方法；该方法接收：

- 最后一个受信任的指针事件，表示当前帧的渲染点。
- 一个包含颜色和直径设置的 `style` 对象。

结果是，在浏览器默认渲染之前，会以指定的样式代表应用绘制一条委派的墨迹轨迹，直到下次收到 `pointermove` 事件为止。

#### HTML

```html
<canvas id="canvas"></canvas>
<div id="div">委派墨迹轨迹的颜色应与此 div 的颜色匹配。</div>
```

#### CSS

```css
div {
  background-color: lime;
  position: fixed;
  top: 1rem;
  left: 1rem;
}
```

#### JavaScript

```js
const ctx = canvas.getContext("2d");
const presenter = navigator.ink.requestPresenter({ presentationArea: canvas });
let moveCnt = 0;
let style = { color: "lime", diameter: 10 };

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

canvas.addEventListener("pointermove", async (evt) => {
  const pointSize = 10;
  ctx.fillStyle = style.color;
  ctx.fillRect(evt.pageX, evt.pageY, pointSize, pointSize);
  if (moveCnt === 20) {
    const r = getRandomInt(0, 255);
    const g = getRandomInt(0, 255);
    const b = getRandomInt(0, 255);

    style = { color: `rgb(${r} ${g} ${b} / 100%)`, diameter: 10 };
    moveCnt = 0;
    document.getElementById("div").style.backgroundColor =
      `rgb(${r} ${g} ${b} / 60%)`;
  }
  moveCnt += 1;
  await presenter.updateInkTrailStartPoint(evt, style);
});

window.addEventListener("pointerdown", () => {
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height);
});

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```

#### 结果

{{EmbedLiveSample("Drawing an ink trail")}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}