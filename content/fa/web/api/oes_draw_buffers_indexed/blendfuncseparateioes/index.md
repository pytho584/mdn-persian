---
title: "OES_draw_buffers_indexed: blendFuncSeparateiOES() method"
short-title: blendFuncSeparateiOES()
slug: Web/API/OES_draw_buffers_indexed/blendFuncSeparateiOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.blendFuncSeparateiOES
---

{{APIRef("WebGL")}}

متد `blendFuncSeparateiOES()` از افزونهٔ WebGL با نام {{DOMxRef("OES_draw_buffers_indexed")}} مشخص می‌کند که برای یک بافر ترسیمی خاص، هنگام ترکیب پیکسل‌ها برای اجزای RGB و آلفا به‌طور جداگانه از چه تابعی استفاده شود.

برای تنظیم همزمان RGB و آلفا، به {{DOMxRef("OES_draw_buffers_indexed.blendFunciOES()")}} و برای نسخهٔ WebGL 1 این متد، به {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}} مراجعه کنید.

## سینتکس

```js-nolint
blendFuncSeparateiOES(buf, srcRGB, dstRGB, srcAlpha, dstAlpha)
```

### پارامترها

- `buf`
  - : یک عدد صحیح `i` که بافر ترسیمی مرتبط با ثابت `gl.DRAW_BUFFERi` را مشخص می‌کند؛ به [ثابت‌های بافر ترسیمی WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers) مراجعه کنید.
- `srcRGB`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که ضریب عوامل ترکیب مبدأ برای رنگ‌های قرمز، سبز و آبی (RGB) را مشخص می‌کند. همان enumهایی را می‌پذیرد که پارامتر `srcRGB` در {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}} می‌پذیرد.
- `dstRGB`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که ضریب عوامل ترکیب مقصد برای رنگ‌های قرمز، سبز و آبی (RGB) را مشخص می‌کند. همان enumهایی را می‌پذیرد که پارامتر `dstRGB` در {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}} می‌پذیرد.
- `srcAlpha`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که ضریب عامل ترکیب مبدأ برای آلفا را مشخص می‌کند. همان enumهایی را می‌پذیرد که پارامتر `srcAlpha` در {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}} می‌پذیرد.
- `dstAlpha`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که ضریب عامل ترکیب مقصد برای آلفا را مشخص می‌کند. همان enumهایی را می‌پذیرد که پارامتر `srcAlpha` در {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}} می‌پذیرد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- اگر `buf` مقدار معتبری نباشد، خطای `gl.INVALID_VALUE` پرتاب می‌شود.
- اگر `srcRGB`، `dstRGB`، `srcAlpha` یا `dstAlpha` یکی از مقادیر ممکن نباشند، خطای `gl.INVALID_ENUM` پرتاب می‌شود.
- همان محدودیت‌های ترکیب که برای {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}} وجود دارد اعمال می‌شود: اگر یک رنگ ثابت و یک مقدار آلفای ثابت با هم به عنوان عوامل مبدأ و مقصد استفاده شوند، خطای `gl.INVALID_ENUM` پرتاب می‌شود.

## مثال‌ها

### تنظیم و دریافت توابع ترکیب

در ادامه، توابع ترکیب برای بافرهای ترسیمی `gl.DRAW_BUFFER0` (فراخوانی با `buf` برابر 0) و `gl.DRAW_BUFFER1` (فراخوانی با `buf` برابر 1) تنظیم می‌شوند.

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.blendFuncSeparateiOES(0, gl.ONE, gl.ONE, gl.ZERO, gl.ZERO);
ext.blendFuncSeparateiOES(
  1,
  gl.SRC_ALPHA,
  gl.ONE_MINUS_SRC_ALPHA,
  gl.ZERO,
  gl.ZERO,
);
```

برای دریافت توابع ترکیب مربوط به بافرهای ترسیمی `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1`، ثابت‌های `BLEND_SRC_RGB`، `BLEND_SRC_ALPHA`، `BLEND_DST_RGB` و `BLEND_DST_ALPHA` را با استفاده از {{domxref("WebGL2RenderingContext.getIndexedParameter()")}} پرس‌وجو کنید:

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

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{DOMxRef("OES_draw_buffers_indexed.blendFunciOES()")}}
- {{DOMxRef("WebGLRenderingContext.blendFuncSeparate()")}}