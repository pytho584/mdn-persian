```yaml
---
title: "OES_draw_buffers_indexed: blendEquationSeparateiOES() method"
short-title: blendEquationSeparateiOES()
slug: Web/API/OES_draw_buffers_indexed/blendEquationSeparateiOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.blendEquationSeparateiOES
---

{{APIRef("WebGL")}}

متد `blendEquationSeparateiOES()` از افزونه WebGL {{DOMxRef("OES_draw_buffers_indexed")}} معادله‌های ترکیب RGB و آلفا را به‌طور جداگانه برای یک بافر رسم مشخص تنظیم می‌کند.

برای تنظیم هم‌زمان RGB و آلفا به {{DOMxRef("OES_draw_buffers_indexed.blendEquationiOES()")}} و برای نسخه WebGL 1 این متد به {{DOMxRef("WebGLRenderingContext.blendEquationSeparate()")}} مراجعه کنید.

## نحو

```js-nolint
blendEquationSeparateiOES(buf, modeRGB, modeAlpha)
```

### پارامترها

- `buf`
  - : یک عدد صحیح `i` که بافر رسم مرتبط با ثابت `gl.DRAW_BUFFERi` را مشخص می‌کند (به [ثابت‌های بافر رسم WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers) مراجعه کنید).
- `modeRGB`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که نحوه ترکیب مؤلفه‌های رنگی RGB مبدأ و مقصد را مشخص می‌کند. همان enum‌های پارامتر `modeRGB` در {{DOMxRef("WebGLRenderingContext.blendEquationSeparate()")}} را می‌پذیرد.
- `modeAlpha`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که نحوه ترکیب مؤلفه‌های رنگی آلفا مبدأ و مقصد را مشخص می‌کند. همان enum‌های پارامتر `modeAlpha` در {{DOMxRef("WebGLRenderingContext.blendEquationSeparate()")}} را می‌پذیرد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- اگر `buf` مقدار معتبری نباشد، خطای `gl.INVALID_VALUE` پرتاب می‌شود.
- اگر `modeRGB` یا `modeAlpha` روی یکی از مقادیر ممکن تنظیم نشده باشند، خطای `gl.INVALID_ENUM` پرتاب می‌شود.

## مثال‌ها

### تنظیم و دریافت معادله‌های ترکیب

در مثال زیر، معادله‌های ترکیب برای بافرهای رسم `gl.DRAW_BUFFER0` (فراخوانی با `buf` برابر ۰) و `gl.DRAW_BUFFER1` (فراخوانی با `buf` برابر ۱) تنظیم می‌شوند.

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.blendEquationSeparateiOES(0, gl.FUNC_ADD, gl.FUNC_SUBTRACT);
ext.blendEquationSeparateiOES(1, gl.FUNC_ADD, gl.FUNC_SUBTRACT);
```

برای دریافت معادله‌های ترکیب `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1`، ثابت‌های `BLEND_EQUATION_RGB` و `BLEND_EQUATION_ALPHA` را با استفاده از {{domxref("WebGL2RenderingContext.getIndexedParameter()")}} پرس‌وجو کنید:

```js
// برای gl.DRAW_BUFFER0
gl.getIndexedParameter(gl.BLEND_EQUATION_RGB, 0);
gl.getIndexedParameter(gl.BLEND_EQUATION_ALPHA, 0);

// برای gl.DRAW_BUFFER1
gl.getIndexedParameter(gl.BLEND_EQUATION_RGB, 1);
gl.getIndexedParameter(gl.BLEND_EQUATION_ALPHA, 1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("OES_draw_buffers_indexed.blendEquationiOES()")}}
- {{DOMxRef("WebGLRenderingContext.blendEquationSeparate()")}}
```