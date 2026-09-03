---
title: "OES_texture_float_linear extension"
short-title: OES_texture_float_linear
slug: Web/API/OES_texture_float_linear
page-type: webgl-extension
browser-compat: api.OES_texture_float_linear
---

{{APIRef("WebGL")}}

افزونه **`OES_texture_float_linear`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و امکان فیلتر خطی (linear filtering) با انواع پیکسل ممیز شناور (floating-point) را برای بافت‌ها فراهم می‌کند.

افزونه‌های WebGL با استفاده از روش {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [Using Extensions](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [WebGL tutorial](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه برای هر دو زمینه {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} و {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است.

## فیلتر خطی

افزونه {{domxref("OES_texture_float")}} به تنهایی اجازه فیلتر خطی با بافت‌های ممیز شناور را نمی‌دهد. این افزونه این قابلیت را فعال می‌کند.

با کمک این افزونه، اکنون می‌توانید فیلتر بزرگنمایی یا کوچک‌نمایی را در روش {{domxref("WebGLRenderingContext.texParameter()")}} به یکی از مقادیر `gl.LINEAR`، `gl.LINEAR_MIPMAP_NEAREST`، `gl.NEAREST_MIPMAP_LINEAR` یا `gl.LINEAR_MIPMAP_LINEAR` تنظیم کرده و از بافت‌های ممیز شناور استفاده کنید.

## مثال

```js
gl.getExtension("OES_texture_float");
gl.getExtension("OES_texture_float_linear");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.texParameterf(gl.TEXTURE_2D, gl.TEXTURE_MAG_FILTER, gl.LINEAR);
gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.FLOAT, image);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
- {{domxref("WebGLRenderingContext.texSubImage2D()")}}
- {{domxref("OES_texture_float")}}
- {{domxref("OES_texture_half_float")}}
- {{domxref("OES_texture_half_float_linear")}}