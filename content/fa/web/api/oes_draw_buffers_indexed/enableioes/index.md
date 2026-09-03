---
title: "OES_draw_buffers_indexed: enableiOES() method"
short-title: enableiOES()
slug: Web/API/OES_draw_buffers_indexed/enableiOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.enableiOES
---

{{APIRef("WebGL")}}

متد `enableiOES()` از افزونه WebGL {{DOMxRef("OES_draw_buffers_indexed")}}، ترکیب (blending) را برای یک بافر رسم خاص فعال می‌کند.

## Syntax

```js-nolint
enableiOES(target, index)
```

### Parameters

- `target`
  - : باید `gl.BLEND` باشد.
- `index`
  - : یک عدد صحیح `i` که بافر رسم مرتبط با ثابت `gl.DRAW_BUFFERi` را مشخص می‌کند. به [ثابت‌های بافر رسم WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers) مراجعه کنید.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Exceptions

- اگر `target` برابر `gl.BLEND` نباشد، خطای `gl.INVALID_ENUM` پرتاب می‌شود.
- اگر `index` مقدار معتبری نباشد، خطای `gl.INVALID_VALUE` پرتاب می‌شود.

## Examples

### فعال‌سازی ترکیب برای بافرهای رسم

دو فراخوانی زیر ترکیب را برای بافرهای رسم `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1` فعال می‌کنند.

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.enableiOES(gl.BLEND, 0);
ext.enableiOES(gl.BLEND, 1);
```

می‌توانید از {{domxref("WebGLRenderingContext.getParameter()")}} برای مشاهده تعداد بافرهای رسم موجود استفاده کنید.

```js
const maxDrawBuffers = gl.getParameter(gl.MAX_DRAW_BUFFERS);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("OES_draw_buffers_indexed.disableiOES()")}}
- [ثابت‌های بافر رسم WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers)