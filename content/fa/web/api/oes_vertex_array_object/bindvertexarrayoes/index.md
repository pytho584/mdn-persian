---
title: "OES_vertex_array_object: bindVertexArrayOES() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/OES_vertex_array_object/bindVertexArrayOES"
---

---
title: "OES_vertex_array_object: bindVertexArrayOES() method"
short-title: bindVertexArrayOES()
slug: Web/API/OES_vertex_array_object/bindVertexArrayOES
page-type: webgl-extension-method
browser-compat: api.OES_vertex_array_object.bindVertexArrayOES
---

{{APIRef("WebGL")}}

متد **`OES_vertex_array_object.bindVertexArrayOES()`** از
[WebGL API](/en-US/docs/Web/API/WebGL_API) یک شیء
{{domxref("WebGLVertexArrayObject")}} داده‌شده را به بافر متصل می‌کند.

## نحو (Syntax)

```js-nolint
bindVertexArrayOES(arrayObject)
```

### پارامترها

- `arrayObject`
  - : یک شیء {{domxref("WebGLVertexArrayObject")}} (VAO) که باید متصل شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const ext = gl.getExtension("OES_vertex_array_object");
const vao = ext.createVertexArrayOES();
ext.bindVertexArrayOES(vao);

// …
// فراخوانی‌های bindBuffer یا vertexAttribPointer
// که در VAO «ثبت» خواهند شد
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.vertexAttribPointer()")}}
- معادل WebGL2: {{domxref("WebGL2RenderingContext.bindVertexArray()")}}