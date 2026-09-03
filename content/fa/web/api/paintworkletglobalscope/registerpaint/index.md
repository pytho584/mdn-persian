---
title: "PaintWorkletGlobalScope: registerPaint() method"
short-title: registerPaint()
slug: Web/API/PaintWorkletGlobalScope/registerPaint
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PaintWorkletGlobalScope.registerPaint
---

{{APIRef("CSS Painting API")}}{{SeeCompatTable}}

{{domxref("PaintWorkletGlobalScope")}} 接口的 **`registerPaint()`** 方法用于注册一个类，以便在 CSS 属性需要图像时以编程方式生成该图像。

## 语法

```js-nolint
registerPaint(name, classRef)
```

### 参数

- `name`
  - : 要注册的 worklet 类的名称。
- `classRef`
  - : 对实现该 worklet 的类的引用。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- {{jsxref("TypeError")}}
  - : 当任一参数无效或缺失时抛出。
- `InvalidModificationError` {{domxref("DOMException")}}
  - : 当指定名称的 worklet 已存在时抛出。

## 示例

以下示例演示了如何注册一个示例 worklet 模块。该代码应放在一个独立的 js 文件中。请注意，`registerPaint()` 调用时没有引用 `PaintWorkletGlobalScope`。该文件本身通过 `CSS.paintWorklet.addModule()` 加载（参见 PaintWorklet 的父类 {{domxref('Worklet.addModule()')}} 中的文档）。

```js
/* checkboardWorklet.js */

class CheckerboardPainter {
  paint(ctx, geom, properties) {
    // Use `ctx` as if it was a normal canvas
    const colors = ["red", "green", "blue"];
    const size = 32;
    for (let y = 0; y < geom.height / size; y++) {
      for (let x = 0; x < geom.width / size; x++) {
        const color = colors[(x + y) % colors.length];
        ctx.beginPath();
        ctx.fillStyle = color;
        ctx.rect(x * size, y * size, size, size);
        ctx.fill();
      }
    }
  }
}

// Register our class under a specific name
registerPaint("checkerboard", CheckerboardPainter);
```

使用 paint worklet 的第一步是像上面那样，通过 `registerPaint()` 函数定义 paint worklet。要使用它，你需要用 `CSS.paintWorklet.addModule()` 方法将其注册：

```js
CSS.paintWorklet.addModule("checkboardWorklet.js");
```

然后，你可以在 CSS 中任何接受 {{cssxref('&lt;image&gt;')}} 值的地方，使用 {{cssxref('image/paint', 'paint()')}} CSS 函数。

```css
li {
  background-image: paint(checkerboard);
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API)
- [Houdini APIs](/en-US/docs/Web/API/Houdini_APIs)