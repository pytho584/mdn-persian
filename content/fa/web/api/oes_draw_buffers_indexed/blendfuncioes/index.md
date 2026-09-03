---
title: "OES_draw_buffers_indexed: blendFunciOES() method"
short-title: blendFunciOES()
slug: Web/API/OES_draw_buffers_indexed/blendFunciOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.blendFunciOES
---

{{APIRef("WebGL")}}

متد `blendFunciOES()` از افزونه‌ی WebGL به نام {{DOMxRef("OES_draw_buffers_indexed")}} مشخص می‌کند که از کدام تابع برای ترکیب پیکسل‌ها برای یک بافر رسم خاص استفاده شود.

برای تنظیم جداگانه مؤلفه‌های RGB و آلفا به {{DOMxRef("OES_draw_buffers_indexed.blendFuncSeparateiOES()")}} و برای نسخه‌ی WebGL 1 این متد به {{DOMxRef("WebGLRenderingContext.blendFunc()")}} مراجعه کنید.

## نحو

```js-nolint
blendFunciOES(buf, src, dst)
```

### پارامترها

- `buf`
  - : یک عدد صحیح `i` که بافر رسم مرتبط با ثابت `gl.DRAW_BUFFERi` را مشخص می‌کند. به [ثابت‌های بافر رسم WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers) مراجعه کنید.
- `src`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که ضریبی برای عوامل ترکیب منبع مشخص می‌کند. همان enum‌های پارامتر `sfactor` در {{DOMxRef("WebGLRenderingContext.blendFunc()")}} را می‌پذیرد.
- `dst`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که ضریبی برای عوامل ترکیب مقصد مشخص می‌کند. همان enum‌های پارامتر `dfactor` در {{DOMxRef("WebGLRenderingContext.blendFunc()")}} را می‌پذیرد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- اگر `buf` مقدار معتبری نباشد، خطای `gl.INVALID_VALUE` پرتاب می‌شود.
- اگر `src` یا `dst` یکی از مقادیر ممکن نباشند، خطای `gl.INVALID_ENUM` پرتاب می‌شود.
- همان محدودیت‌های ترکیب برای {{DOMxRef("WebGLRenderingContext.blendFunc()")}} اعمال می‌شود: اگر یک رنگ ثابت و یک مقدار آلفای ثابت با هم به عنوان عوامل منبع و مقصد استفاده شوند، خطای `gl.INVALID_ENUM` پرتاب می‌شود.

## مثال‌ها

### تنظیم و دریافت توابع ترکیب

می‌توانید توابع ترکیب را برای بافرهای رسم `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1` به این صورت تنظیم کنید:

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.blendFunciOES(0, gl.ONE, gl.ONE);
ext.blendFunciOES(1, gl.SRC_ALPHA, gl.ONE_MINUS_SRC_ALPHA);
```

برای دریافت توابع ترکیب بافرهای رسم `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1`، ثابت‌های `BLEND_SRC_RGB`، `BLEND_SRC_ALPHA`، `BLEND_DST_RGB` و `BLEND_DST_ALPHA` را با استفاده از {{domxref("WebGL2RenderingContext.getIndexedParameter()")}} پرس‌وجو کنید:

```js
// For gl.DRAW_BUFFER0
gl.getIndexedParameter(gl.BLEND_SRC_RGB, 0);
gl.getIndexedParameter(gl.BLEND_SRC_ALPHA, 0);
gl.getIndexedParameter(gl.BLEND_DST_RGB, 0);
gl.getIndexedParameter(gl.BLEND_DST_ALPHA, 0);

// For gl.DRAW_BUFFER0
gl.getIndexedParameter(gl.BLEND_SRC_RGB, 1);
gl.getIndexedParameter(gl.BLEND_SRC_ALPHA, 1);
gl.getIndexedParameter(gl.BLEND_DST_RGB, 1);
gl.getIndexedParameter(gl.BLEND_DST_ALPHA, 1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("OES_draw_buffers_indexed.blendFuncSeparateiOES()")}}
- {{DOMxRef("WebGLRenderingContext.blendFunc()")}}