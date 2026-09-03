---
title: "Performance: eventCounts property"
short-title: eventCounts
slug: Web/API/Performance/eventCounts
page-type: web-api-instance-property
browser-compat: api.Performance.eventCounts
---

{{APIRef("Performance API")}}

خاصیت read-only **`performance.eventCounts`** یک {{domxref("EventCounts")}} map (نقشه) است که تعداد رویدادهای ارسال‌شده به ازای هر نوع رویداد را از زمان بارگذاری صفحه نگه می‌دارد.

همه انواع رویدادها در معرض دید قرار نمی‌گیرند. شما فقط می‌توانید تعداد رویدادهایی را دریافت کنید که توسط رابط {{domxref("PerformanceEventTiming")}} پشتیبانی می‌شوند.

## مقدار

یک {{domxref("EventCounts")}} map.
(یک {{jsxref("Map")}} فقط خواندنی بدون متدهای `clear()`، `delete()` و `set()`).

## مثال‌ها

### گزارش انواع رویدادها و تعدادشان

اگر می‌خواهید تعداد رویدادها را به سامانه تحلیل خود ارسال کنید، می‌توانید تابعی مانند `sendToEventAnalytics` پیاده‌سازی کنید که تعداد رویدادها را از `performance.eventCounts` map گرفته و سپس با استفاده از [Fetch API](/en-US/docs/Web/API/Fetch_API) داده‌ها را به endpoint خود ارسال کند.

```js
// گزارش تمام رویدادهای در معرض دید
for (entry of performance.eventCounts.entries()) {
  const type = entry[0];
  const count = entry[1];
  // sendToEventAnalytics(type, count);
}

// گزارش یک رویداد خاص
const clickCount = performance.eventCounts.get("click");
// sendToEventAnalytics("click", clickCount);

// بررسی کنید که آیا تعداد یک رویداد برای یک نوع خاص در معرض دید است
const isExposed = performance.eventCounts.has("mousemove"); // false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventCounts")}}
- {{domxref("PerformanceEventTiming")}}
- {{jsxref("Map")}}