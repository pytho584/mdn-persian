---
title: "OffscreenCanvas: width property"
short-title: width
slug: Web/API/OffscreenCanvas/width
page-type: web-api-instance-property
browser-compat: api.OffscreenCanvas.width
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی **`width`** عرض یک شیء {{domxref("OffscreenCanvas")}} را برمی‌گرداند و تنظیم می‌کند.

## مقدار

یک عدد صحیح مثبت که عرض بوم خارج از صفحه را بر حسب پیکسل CSS نشان می‌دهد.

## مثال‌ها

ایجاد یک بوم خارج از صفحه جدید و برگرداندن یا تنظیم عرض آن:

```js
const offscreen = new OffscreenCanvas(256, 256);
offscreen.width; // 256
offscreen.width = 512;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("OffscreenCanvas")}}، واسطی که این ویژگی به آن تعلق دارد.