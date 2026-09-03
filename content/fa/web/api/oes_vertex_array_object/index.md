---
title: OES_vertex_array_object extension
short-title: OES_vertex_array_object
slug: Web/API/OES_vertex_array_object
page-type: webgl-extension
browser-compat: api.OES_vertex_array_object
---

{{APIRef("WebGL")}}

افزونهٔ **OES_vertex_array_object** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و شیءهای آرایه رأس (VAO) را فراهم می‌کند که وضعیت آرایه رأس را در خود کپسوله می‌کنند. این شیءها اشاره‌گرهایی به داده‌های رأس نگه می‌دارند و نام‌هایی برای مجموعه‌های مختلف داده رأس ارائه می‌دهند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، همچنین [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) را در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) ببینید.

> [!NOTE]
> این افزونه فقط برای زمینه‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌صورت پیش‌فرض روی زمینهٔ WebGL2 موجود است و ثابت‌ها و روش‌ها بدون پسوندِ `OES_` در دسترس هستند.

## ثابت‌ها

این افزونه یک ثابت جدید ارائه می‌دهد که می‌توان در متد {{domxref("WebGLRenderingContext.getParameter()", "gl.getParameter()")}} از آن استفاده کرد:

- `ext.VERTEX_ARRAY_BINDING_OES`
  - : وقتی در متد {{domxref("WebGLRenderingContext.getParameter()", "gl.getParameter()")}} به‌عنوان پارامتر `pname` استفاده شود، یک شیء {{domxref("WebGLVertexArrayObject")}} برمی‌گرداند.

## روش‌های نمونه

این افزونه چهار روش جدید ارائه می‌دهد.

- {{domxref("OES_vertex_array_object.createVertexArrayOES()", "ext.createVertexArrayOES()")}}
  - : یک {{domxref("WebGLVertexArrayObject")}} جدید ایجاد می‌کند.
- {{domxref("OES_vertex_array_object.deleteVertexArrayOES()", "ext.deleteVertexArrayOES()")}}
  - : یک {{domxref("WebGLVertexArrayObject")}} معین را حذف می‌کند.
- {{domxref("OES_vertex_array_object.isVertexArrayOES()", "ext.isVertexArrayOES()")}}
  - : اگر شیء داده‌شده یک {{domxref("WebGLVertexArrayObject")}} باشد، `true` برمی‌گرداند.
- {{domxref("OES_vertex_array_object.bindVertexArrayOES()", "ext.bindVertexArrayOES()")}}
  - : یک {{domxref("WebGLVertexArrayObject")}} معین را به بافر متصل می‌کند.

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
- متدهای معادل در WebGL2:
  - {{domxref("WebGL2RenderingContext.createVertexArray()")}}
  - {{domxref("WebGL2RenderingContext.deleteVertexArray()")}}
  - {{domxref("WebGL2RenderingContext.isVertexArray()")}}
  - {{domxref("WebGL2RenderingContext.bindVertexArray()")}}