---
title: "OES_vertex_array_object: deleteVertexArrayOES() method"
short-title: deleteVertexArrayOES()
slug: Web/API/OES_vertex_array_object/deleteVertexArrayOES
page-type: webgl-extension-method
browser-compat: api.OES_vertex_array_object.deleteVertexArrayOES
---

{{APIRef("WebGL")}}

متد **`OES_vertex_array_object.deleteVertexArrayOES()`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) یک شیء {{domxref("WebGLVertexArrayObject")}} مشخص را حذف می‌کند.

## سینتکس

```js-nolint
deleteVertexArrayOES(arrayObject)
```

### پارامترها

- `arrayObject`
  - : یک شیء {{domxref("WebGLVertexArrayObject")}} (VAO) که باید حذف شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const ext = gl.getExtension("OES_vertex_array_object");
const vao = ext.createVertexArrayOES();
ext.bindVertexArrayOES(vao);

// …

ext.deleteVertexArrayOES(vao);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.vertexAttribPointer()")}}
- معادل WebGL2: {{domxref("WebGL2RenderingContext.deleteVertexArray()")}}