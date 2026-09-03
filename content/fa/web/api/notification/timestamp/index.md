---
title: "Notification: timestamp property"
short-title: timestamp
slug: Web/API/Notification/timestamp
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Notification.timestamp
---

{{APIRef("Web Notifications")}}{{SecureContext_Header}}{{SeeCompatTable}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`timestamp`** در رابط {{domxref("Notification")}} عددی را برمی‌گرداند که مقدارش مطابق گزینهٔ `timestamp` در سازندهٔ {{domxref("Notification.Notification","Notification()")}} تعیین می‌شود.

برچسب زمانیِ اعلان می‌تواند زمانِ رویدادی را نشان دهد که اعلان برای آن ساخته شده است؛ این زمان بر حسب میلی‌ثانیه از ۰۰:۰۰:۰۰ UTC در ۱ ژانویهٔ ۱۹۷۰ سنجیده می‌شود. همچنین می‌تواند یک برچسب زمانیِ دلخواه باشد که بخواهید آن را با اعلان مرتبط کنید. برای نمونه، برچسب زمانی یک جلسهٔ آینده را می‌توان در آینده تنظیم کرد؛ در حالی که برچسب زمانی یک پیام از دست‌رفته را می‌توان در گذشته قرار داد.

## مقدار

عددی که یک برچسب زمانی را نشان می‌دهد و به‌صورت {{Glossary("Unix time")}} بر حسب میلی‌ثانیه بیان می‌شود.

## نمونه‌ها

قطعه‌کد زیر یک اعلان را اجرا می‌کند؛ یک شیء سادهٔ `options` ساخته می‌شود و سپس اعلان با استفاده از سازندهٔ `Notification()` ارسال می‌شود.

```js
const dts = Math.floor(Date.now());

const options = {
  body: "Your code submission has received 3 new review comments.",
  timestamp: dts,
};

const n = new Notification("New review activity", options);

console.log(n.timestamp); // Logs the timestamp
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)