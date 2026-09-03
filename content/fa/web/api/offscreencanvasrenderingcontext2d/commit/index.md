---
title: "OffscreenCanvasRenderingContext2D: commit() method"
short-title: commit()
slug: Web/API/OffscreenCanvasRenderingContext2D/commit
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.OffscreenCanvasRenderingContext2D.commit
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}{{deprecated_header}}{{non-standard_header}}

متد **`OffscreenCanvasRenderingContext2D.commit()`** از [Canvas 2D API](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D) قرار بود بیت‌مپِ زمینهٔ رندر را در بیت‌مپِ عنصر {{HtmlElement("canvas")}} جایگزینِ مرتبط با آبجکت `OffscreenCanvas` کپی کند. عملیات کپی به‌صورت همگام (synchronous) انجام می‌شود. برای انجام این انتقال نیازی به فراخواندن این متد نیست؛ زیرا این انتقال به‌طور خودکار هنگام اجرای حلقهٔ رویداد (event loop) صورت می‌گیرد.

## نحو

```js-nolint
commit()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const placeholder = document.createElement("canvas");
const offscreen = placeholder.transferControlToOffscreen();
const ctx = offscreenCanvas.getContext("2d");

// Perform some drawing using the 2d context
ctx.fillStyle = "blue";
ctx.fillRect(0, 0, 10, 10);

// Push placeholder to the canvas element
ctx.commit();
```

## مشخصات

این متد بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("OffscreenCanvasRenderingContext2D")}}