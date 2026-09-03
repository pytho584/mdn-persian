---
title: "OES_draw_buffers_indexed: colorMaskiOES() method"
short-title: colorMaskiOES()
slug: Web/API/OES_draw_buffers_indexed/colorMaskiOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.colorMaskiOES
---

{{APIRef("WebGL")}}

`colorMaskiOES()` 方法（属于 {{DOMxRef("OES_draw_buffers_indexed")}} WebGL 扩展）用于设置在绘制或渲染到特定绘制缓冲区时，哪些颜色分量应被启用或禁用。它是 WebGL 1 中 {{domxref("WebGLRenderingContext.colorMask()")}} 方法的索引版本。

## 语法

```js-nolint
colorMaskiOES(buf, r, g, b, a)
```

### 参数

- `buf`
  - : 一个整数 `i`，指定与常量 `gl.DRAW_BUFFERi` 关联的绘制缓冲区，参见 [WebGL 绘制缓冲区常量](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers)。

- `r`
  - : 一个 {{domxref("WebGL_API/Types", "GLboolean")}}，指定红色分量是否应写入绘制缓冲区。

- `g`
  - : 一个 {{domxref("WebGL_API/Types", "GLboolean")}}，指定绿色分量是否应写入绘制缓冲区。

- `b`
  - : 一个 {{domxref("WebGL_API/Types", "GLboolean")}}，指定蓝色分量是否应写入绘制缓冲区。

- `a`
  - : 一个 {{domxref("WebGL_API/Types", "GLboolean")}}，指定 alpha（透明度）分量是否应写入绘制缓冲区。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- 如果 `buf`、`r`、`g`、`b` 或 `a` 不是有效值，则会抛出 `gl.INVALID_VALUE` 错误。

## 示例

### 设置和获取颜色掩码

你可以这样为 `gl.DRAW_BUFFER0` 和 `gl.DRAW_BUFFER1` 绘制缓冲区设置颜色掩码：

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.colorMaskiOES(0, 1, 0, 0, 0);
ext.colorMaskiOES(1, 0, 1, 0, 0);
```

要获取 `gl.DRAW_BUFFER0` 和 `gl.DRAW_BUFFER1` 绘制缓冲区的颜色掩码，可以使用 {{domxref("WebGL2RenderingContext.getIndexedParameter()")}} 查询 `COLOR_WRITEMASK` 常量：

```js
gl.getIndexedParameter(gl.COLOR_WRITEMASK, 0);
gl.getIndexedParameter(gl.COLOR_WRITEMASK, 1);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("WebGL2RenderingContext.getIndexedParameter()")}}
- {{domxref("WebGLRenderingContext.colorMask()")}}