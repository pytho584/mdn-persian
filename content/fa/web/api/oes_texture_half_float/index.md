---
title: OES_texture_half_float extension
short-title: OES_texture_half_float
slug: Web/API/OES_texture_half_float
page-type: webgl-extension
browser-compat: api.OES_texture_half_float
---

{{APIRef("WebGL")}}

افزونهٔ **`OES_texture_half_float`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و قالب‌های بافت با مؤلفه‌های ممیز شناور ۱۶ بیتی (نیمه‌اعشاری) و ۳۲ بیتی را اضافه می‌کند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه تنها در زمینه‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} قابل استفاده است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌طور پیش‌فرض در دسترس است. ثابت مربوطه در WebGL2 `gl.HALF_FLOAT` است.

## ثابت‌ها

- `ext.HALF_FLOAT_OES`
  - : نوع ممیز شناور نیمه‌اعشاری (16 بیتی).

## متدهای گسترش‌یافته

این افزونه متد‌های {{domxref("WebGLRenderingContext.texImage2D()")}} و {{domxref("WebGLRenderingContext.texSubImage2D()")}} را گسترش می‌دهد:

- پارامتر `type` اکنون مقدار `ext.HALF_FLOAT_OES` را می‌پذیرد.

## محدودیت: فیلتر خطی

فیلتر خطی روی بافت‌های ممیز شناور نیمه‌اعشاری با این افزونه مجاز نیست. اگر در متد {{domxref("WebGLRenderingContext.texParameter()")}} فیلتر بزرگ‌نمایی یا کوچک‌نمایی را روی یکی از مقادیر `gl.LINEAR`، `gl.LINEAR_MIPMAP_NEAREST`، `gl.NEAREST_MIPMAP_LINEAR` یا `gl.LINEAR_MIPMAP_LINEAR` تنظیم کنید و از بافت‌های نیمه‌اعشاری استفاده کنید، بافت ناقص علامت‌گذاری می‌شود.

برای استفاده از فیلتر خطی روی بافت‌های نیمه‌اعشاری، افزونهٔ {{domxref("OES_texture_half_float_linear")}} را علاوه بر این افزونه فعال کنید.

## بافرهای رنگی ممیز شناور نیمه‌اعشاری

این افزونه به‌طور ضمنی افزونهٔ {{domxref("EXT_color_buffer_half_float")}} (در صورت پشتیبانی) را فعال می‌کند که امکان رندر کردن به قالب‌های ممیز شناور ۱۶ بیتی را فراهم می‌کند.

## مثال

```js
const ext = gl.getExtension("OES_texture_half_float");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, ext.HALF_FLOAT_OES, image);
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
- {{domxref("OES_texture_float_linear")}}
- {{domxref("OES_texture_half_float_linear")}}