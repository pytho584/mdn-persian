---
title: OES_element_index_uint extension
short-title: OES_element_index_uint
slug: Web/API/OES_element_index_uint
page-type: webgl-extension
browser-compat: api.OES_element_index_uint
---

{{APIRef("WebGL")}}

افزونهٔ **`OES_element_index_uint`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و پشتیبانی از نوع `gl.UNSIGNED_INT` را به {{domxref("WebGLRenderingContext.drawElements()")}} اضافه می‌کند.

افزونه‌های WebGL از طریق روش {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط در زمینه‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، قابلیت‌های این افزونه به‌صورت پیش‌فرض در زمینهٔ WebGL2 موجود است.

## روش‌های توسعه‌یافته

این افزونه {{domxref("WebGLRenderingContext.drawElements()")}} را گسترش می‌دهد:

- پارامتر `type` اکنون مقدار `gl.UNSIGNED_INT` را می‌پذیرد.

## مثال‌ها

```js
const ext = gl.getExtension("OES_element_index_uint");

gl.drawElements(gl.POINTS, 8, gl.UNSIGNED_INT, 0);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.drawElements()")}}