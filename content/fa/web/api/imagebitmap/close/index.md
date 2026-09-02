---
title: "ImageBitmap: close() method"
short-title: close()
slug: Web/API/ImageBitmap/close
page-type: web-api-instance-method
browser-compat: api.ImageBitmap.close
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`ImageBitmap.close()`** همهٔ منابع گرافیکی مرتبط با یک `ImageBitmap` را آزاد می‌کند.

## نحو

```js-nolint
close()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// Perform some drawing using the gl context

const bitmap = offscreen.transferToImageBitmap();
// ImageBitmap { width: 256, height: 256 }

bitmap.close();
// ImageBitmap { width: 0, height: 0 } — disposed
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("ImageBitmap")}}