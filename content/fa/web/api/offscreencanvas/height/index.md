---
title: "OffscreenCanvas: height property"
short-title: height
slug: Web/API/OffscreenCanvas/height
page-type: web-api-instance-property
browser-compat: api.OffscreenCanvas.height
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی **`height`** ارتفاع یک شیء {{domxref("OffscreenCanvas")}} را بازمی‌گرداند و تنظیم می‌کند.

## مقدار

یک عدد صحیح مثبت که ارتفاع بوم خارج از صفحه (offscreen canvas) را بر حسب پیکسل‌های CSS نشان می‌دهد.

## مثال‌ها

ایجاد یک بوم خارج از صفحه جدید و بازگرداندن یا تنظیم ارتفاع آن:

```js
const offscreen = new OffscreenCanvas(256, 256);
offscreen.height; // 256
offscreen.height = 512;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("OffscreenCanvas")}}، واسطی که این ویژگی به آن تعلق دارد.