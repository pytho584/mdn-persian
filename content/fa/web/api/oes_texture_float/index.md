---
title: OES_texture_float extension
short-title: OES_texture_float
slug: Web/API/OES_texture_float
page-type: webgl-extension
browser-compat: api.OES_texture_float
---

{{APIRef("WebGL")}}

افزونهٔ **`OES_texture_float`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و نوع داده‌ی پیکسل‌های ممیز شناور را برای بافت‌ها فراهم می‌کند.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط در دسترس بافت‌های (context) {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} قرار دارد. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌طور پیش‌فرض در بافت WebGL2 موجود است.

## متدهای توسعه داده‌شده

این افزونه، متدهای {{domxref("WebGLRenderingContext.texImage2D()")}} و {{domxref("WebGLRenderingContext.texSubImage2D()")}} را توسعه می‌دهد:

- پارامتر `type` اکنون مقدار `gl.FLOAT` را می‌پذیرد.
- پارامتر `pixels` اکنون یک {{jsxref("Float32Array")}} را می‌پذیرد.

## محدودیت: فیلتر خطی (Linear filtering)

فیلتر خطی روی بافت‌های ممیز شناور با این افزونه مجاز نیست. اگر در متد {{domxref("WebGLRenderingContext.texParameter()")}} فیلتر بزرگ‌نمایی یا کوچک‌نمایی را روی یکی از مقادیر `gl.LINEAR`، `gl.LINEAR_MIPMAP_NEAREST`، `gl.NEAREST_MIPMAP_LINEAR` یا `gl.LINEAR_MIPMAP_LINEAR` قرار دهید و از بافت‌های ممیز شناور استفاده کنید، بافت به‌عنوان ناقص (incomplete) علامت‌گذاری می‌شود.

برای استفاده از فیلتر خطی روی بافت‌های ممیز شناور، افزونهٔ {{domxref("OES_texture_float_linear")}} را علاوه بر این افزونه فعال کنید.

## بافرهای رنگی ممیز شناور

این افزونه به‌طور ضمنی افزونهٔ {{domxref("WEBGL_color_buffer_float")}} را (در صورت پشتیبانی) فعال می‌کند که امکان رندر به بافرهای رنگی ۳۲بیتی ممیز شناور را فراهم می‌کند.

## مثال‌ها

```js
const ext = gl.getExtension("OES_texture_float");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.FLOAT, image);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
- {{domxref("WebGLRenderingContext.texSubImage2D()")}}
- {{domxref("OES_texture_float_linear")}}
- {{domxref("OES_texture_half_float")}}
- {{domxref("OES_texture_half_float_linear")}}