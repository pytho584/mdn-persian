---
title: "OES_vertex_array_object: createVertexArrayOES() method"
short-title: createVertexArrayOES()
slug: Web/API/OES_vertex_array_object/createVertexArrayOES
page-type: webgl-extension-method
browser-compat: api.OES_vertex_array_object.createVertexArrayOES
---

{{APIRef("WebGL")}}

متد **`OES_vertex_array_object.createVertexArrayOES()`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) یک شیء {{domxref("WebGLVertexArrayObject")}} ایجاد و مقداردهی اولیه می‌کند. این شیء، یک شیء آرایه رأس (VAO) را نشان می‌دهد که به داده‌های آرایهٔ رأس اشاره می‌کند و برای مجموعه‌های مختلف داده‌های رأس، نام‌هایی فراهم می‌کند.

## نحو

```js-nolint
createVertexArrayOES()
```

### پارامترها

هیچ پارامتری ندارد.

### مقدار بازگشتی

یک {{domxref("WebGLVertexArrayObject")}} که نشان‌دهندهٔ یک شیء آرایه رأس (VAO) است و به داده‌های آرایهٔ رأس اشاره می‌کند.

## مثال‌ها

```js
const ext = gl.getExtension("OES_vertex_array_object");
const vao = ext.createVertexArrayOES();
ext.bindVertexArrayOES(vao);

// …
// calls to bindBuffer or vertexAttribPointer
// which will be "recorded" in the VAO
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.vertexAttribPointer()")}}
- معادل WebGL2: {{domxref("WebGL2RenderingContext.createVertexArray()")}}