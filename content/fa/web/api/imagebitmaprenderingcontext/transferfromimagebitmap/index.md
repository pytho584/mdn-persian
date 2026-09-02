---
title: "ImageBitmapRenderingContext: transferFromImageBitmap() method"
short-title: transferFromImageBitmap()
slug: Web/API/ImageBitmapRenderingContext/transferFromImageBitmap
page-type: web-api-instance-method
browser-compat: api.ImageBitmapRenderingContext.transferFromImageBitmap
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`ImageBitmapRenderingContext.transferFromImageBitmap()`**، {{domxref("ImageBitmap")}} داده‌شده را در بوم (canvas) مرتبط با این زمینهٔ رندرگیری نمایش می‌دهد. مالکیتِ آن `ImageBitmap` نیز به بوم منتقل می‌شود.

این متد پیش از این `transferImageBitmap()` نام داشت، اما در یک تغییر در مشخصات (spec) تغییر نام داد. برای جلوگیری از شکستن کدهای موجود، نام قدیمی همچنان به‌عنوان یک نام مستعار (alias) حفظ شده است.

## سینتکس

```js-nolint
transferFromImageBitmap(bitmap)
```

### پارامترها

- `bitmap`
  - : یک شیء {{domxref("ImageBitmap")}} برای انتقال، یا `null`. اگر مقدار `null` باشد، بوم به حالت خالی بازنشانی می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### HTML

```html
<canvas id="htmlCanvas"></canvas>
```

### JavaScript

```js
const htmlCanvas = document
  .getElementById("htmlCanvas")
  .getContext("bitmaprenderer");

// Draw a WebGL scene offscreen
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// Perform some drawing using the gl context

// Transfer the current frame to the visible canvas
const bitmap = offscreen.transferToImageBitmap();
htmlCanvas.transferFromImageBitmap(bitmap);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("ImageBitmapRenderingContext")}}
- {{domxref("OffscreenCanvas")}}
- {{domxref("OffscreenCanvas.transferToImageBitmap()")}}