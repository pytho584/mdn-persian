---
title: OES_texture_half_float_linear extension
short-title: OES_texture_half_float_linear
slug: Web/API/OES_texture_half_float_linear
page-type: webgl-extension
browser-compat: api.OES_texture_half_float_linear
---

{{APIRef("WebGL")}}

افزونهٔ **`OES_texture_half_float_linear`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و فیلتر خطی را برای انواع پیکسل ممیز شناورِ نصفه (half floating-point) در بافت‌ها فراهم می‌کند.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) نیز مراجعه کنید.

> [!NOTE]
> این افزونه فقط در زمینه‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌صورت پیش‌فرض در زمینهٔ WebGL2 موجود است و نیازی به این افزونه نیست.

## فیلتر خطی

افزونهٔ {{domxref("OES_texture_half_float")}} به تنهایی اجازهٔ فیلتر خطی با بافت‌های ممیز شناورِ نصفه را نمی‌دهد. این افزونه این قابلیت را فعال می‌کند.

با کمک این افزونه، اکنون می‌توانید فیلتر بزرگنمایی یا کوچک‌نمایی را در متد {{domxref("WebGLRenderingContext.texParameter()")}} روی یکی از مقادیر `gl.LINEAR`، `gl.LINEAR_MIPMAP_NEAREST`، `gl.NEAREST_MIPMAP_LINEAR` یا `gl.LINEAR_MIPMAP_LINEAR` تنظیم کنید و از بافت‌های ممیز شناورِ نصفه استفاده کنید.

## مثال

```js
const halfFloat = gl.getExtension("OES_texture_half_float");
gl.getExtension("OES_texture_half_float_linear");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.texParameterf(gl.TEXTURE_2D, gl.TEXTURE_MAG_FILTER, gl.LINEAR);
gl.texImage2D(
  gl.TEXTURE_2D,
  0,
  gl.RGBA,
  gl.RGBA,
  halfFloat.HALF_FLOAT_OES,
  image,
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
- {{domxref("WebGLRenderingContext.texSubImage2D()")}}
- {{domxref("OES_texture_float")}}
- {{domxref("OES_texture_float_linear")}}
- {{domxref("OES_texture_half_float")}}