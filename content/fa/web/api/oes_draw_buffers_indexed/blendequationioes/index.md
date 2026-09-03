---
title: "OES_draw_buffers_indexed: blendEquationiOES() method"
---
---
title: "OES_draw_buffers_indexed: blendEquationiOES() method"
short-title: blendEquationiOES()
slug: Web/API/OES_draw_buffers_indexed/blendEquationiOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.blendEquationiOES
---

{{APIRef("WebGL")}}

روش `blendEquationiOES()` در افزونهٔ WebGL با نام `OES_draw_buffers_indexed`، معادلات ترکیب RGB و آلفا را برای یک بافر ترسیمی مشخص تنظیم می‌کند.

برای تنظیم جداگانهٔ RGB و آلفا به {{DOMxRef("OES_draw_buffers_indexed.blendEquationSeparateiOES()")}} و برای نسخهٔ WebGL 1 این روش به {{DOMxRef("WebGLRenderingContext.blendEquation()")}} مراجعه کنید.

## Syntax

```js-nolint
blendEquationiOES(buf, mode)
```

### Parameters

- `buf`
  - : یک عدد صحیح `i` که بافر ترسیمی مرتبط با ثابت `gl.DRAW_BUFFERi` را مشخص می‌کند؛ به [ثابت‌های بافر ترسیمی WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers) مراجعه کنید.
- `mode`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که نحوهٔ ترکیب رنگ مبدأ و مقصد را مشخص می‌کند. همان enumهای پارامتر `mode` در {{DOMxRef("WebGLRenderingContext.blendEquation()")}} را می‌پذیرد.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- اگر `buf` مقدار معتبری نباشد، خطای `gl.INVALID_VALUE` پرتاب می‌شود.
- اگر `mode` یکی از مقادیر ممکن نباشد، خطای `gl.INVALID_ENUM` پرتاب می‌شود.

## Examples

### تنظیم و دریافت معادلات ترکیب

می‌توانید معادلات ترکیب را برای بافرهای ترسیمی `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1` به این صورت تنظیم کنید:

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.blendEquationiOES(0, gl.FUNC_ADD);
ext.blendEquationiOES(1, gl.FUNC_SUBTRACT);
```

برای دریافت معادلات ترکیب بافرهای ترسیمی `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1`، ثابت‌های `BLEND_EQUATION_RGB` و `BLEND_EQUATION_ALPHA` را با استفاده از {{domxref("WebGL2RenderingContext.getIndexedParameter()")}} پرس‌وجو کنید:

```js
// For gl.DRAW_BUFFER0
gl.getIndexedParameter(gl.BLEND_EQUATION_RGB, 0);
gl.getIndexedParameter(gl.BLEND_EQUATION_ALPHA, 0);

// For gl.DRAW_BUFFER0
gl.getIndexedParameter(gl.BLEND_EQUATION_RGB, 1);
gl.getIndexedParameter(gl.BLEND_EQUATION_ALPHA, 1);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{DOMxRef("OES_draw_buffers_indexed.blendEquationSeparateiOES()")}}
- {{DOMxRef("WebGLRenderingContext.blendEquation()")}}