---
title: "OES_vertex_array_object: isVertexArrayOES() method"
short-title: isVertexArrayOES()
slug: Web/API/OES_vertex_array_object/isVertexArrayOES
page-type: webgl-extension-method
browser-compat: api.OES_vertex_array_object.isVertexArrayOES
---

{{APIRef("WebGL")}}

متد **`OES_vertex_array_object.isVertexArrayOES()`** در [WebGL API](/en-US/docs/Web/API/WebGL_API) اگر شیء ارسال‌شده یک شیء {{domxref("WebGLVertexArrayObject")}} باشد، مقدار `true` را برمی‌گرداند.

## سینتکس

```js-nolint
isVertexArrayOES(arrayObject)
```

### پارامترها

- `arrayObject`
  - : یک شیء {{domxref("WebGLVertexArrayObject")}} (VAO) برای آزمایش.

### مقدار بازگشتی

یک {{domxref("WebGL_API.Types", "GLboolean")}} که نشان می‌دهد آیا شیء داده‌شده یک شیء {{domxref("WebGLVertexArrayObject")}} است (`true`) یا خیر (`false`).

## مثال‌ها

```js
const ext = gl.getExtension("OES_vertex_array_object");
const vao = ext.createVertexArrayOES();
ext.bindVertexArrayOES(vao);

// …

ext.isVertexArrayOES(vao);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.vertexAttribPointer()")}}
- معادل WebGL2: {{domxref("WebGL2RenderingContext.isVertexArray()")}}