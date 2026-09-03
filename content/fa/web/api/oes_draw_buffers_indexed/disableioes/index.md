---
title: "OES_draw_buffers_indexed: disableiOES() method"
---

---
title: "OES_draw_buffers_indexed: disableiOES() method"
short-title: disableiOES()
slug: Web/API/OES_draw_buffers_indexed/disableiOES
page-type: web-api-instance-method
browser-compat: api.OES_draw_buffers_indexed.disableiOES
---

{{APIRef("WebGL")}}

متد `disableiOES()` از افزونهٔ وب‌گل {{DOMxRef("OES_draw_buffers_indexed")}}، ترکیب (blending) را برای یک بافر draw خاص غیرفعال می‌کند.

## سینتکس

```js-nolint
disableiOES(target, index)
```

### پارامترها

- `target`
  - : باید `gl.BLEND` باشد.
- `index`
  - : یک عدد صحیح `i` که بافر draw مرتبط با ثابت `gl.DRAW_BUFFERi` را مشخص می‌کند؛ به [ثابت‌های بافر draw در WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers) مراجعه کنید.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- اگر `target` برابر با `gl.BLEND` نباشد، خطای `gl.INVALID_ENUM` پرتاب می‌شود.
- اگر `index` مقدار معتبری نباشد، خطای `gl.INVALID_VALUE` پرتاب می‌شود.

## مثال‌ها

### غیرفعال کردن ترکیب برای بافرهای draw

دو فراخوانی زیر، ترکیب را برای بافرهای draw یعنی `gl.DRAW_BUFFER0` و `gl.DRAW_BUFFER1` غیرفعال می‌کنند.

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");

ext.disableiOES(gl.BLEND, 0);
ext.disableiOES(gl.BLEND, 1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("OES_draw_buffers_indexed.enableiOES()")}}
- [ثابت‌های بافر draw در WebGL](/en-US/docs/Web/API/WebGL_API/Constants#draw_buffers)