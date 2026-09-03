---
title: "Performance: memory property"
short-title: memory
slug: Web/API/Performance/memory
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Performance.memory
---

{{APIRef("Performance API")}}{{Deprecated_Header}}{{Non-standard_header}}

ویژگی فقط‌خواندنی **`memory`** که غیراستاندارد و قدیمی است، اندازهٔ heap جاوااسکریپت را برمی‌گرداند و می‌تواند برای اندازه‌گیری و کاهش ردپای حافظهٔ وب‌سایت‌ها مفید باشد.

توجه داشته باشید که اطلاعات ارائه‌شده توسط این API قابل اعتماد نیست؛ زیرا اگر صفحات وب heap یکسانی را به اشتراک بگذارند، ممکن است مصرف واقعی حافظه را بیش‌ازحد تخمین بزند، یا اگر صفحات وب از workerها و/یا iframeهای بین‌سایتی استفاده کنند که در heapهای جداگانه تخصیص داده شده‌اند، ممکن است مصرف واقعی حافظه را کمتر از حد واقعی نشان دهد. همچنین مشخص نیست که «heap» دقیقاً به چه معناست. این API فقط در مرورگرهای مبتنی بر Chromium در دسترس است.

API جدیدی که هدف آن جایگزینی `performance.memory` است، {{domxref("Performance.measureUserAgentSpecificMemory()")}} می‌باشد. این API سعی می‌کند حافظهٔ استفاده‌شده توسط یک صفحهٔ وب را تخمین بزند.

## مقدار

یک شیء با ویژگی‌های زیر برمی‌گرداند:

- `jsHeapSizeLimit`
  - : حداکثر اندازهٔ heap بر حسب بایت که در دسترس context قرار دارد.
- `totalJSHeapSize`
  - : کل اندازهٔ heap تخصیص‌یافته بر حسب بایت.
- `usedJSHeapSize`
  - : بخش فعال فعلی heap جاوااسکریپت بر حسب بایت.

## مثال‌ها

### دریافت اندازه‌های heap جاوااسکریپت

فراخوانی `performance.memory` یک شیء مانند زیر برمی‌گرداند:

```json
{
  "totalJSHeapSize": 39973671,
  "usedJSHeapSize": 39127515,
  "jsHeapSizeLimit": 4294705152
}
```

## مشخصات

هیچ‌کدام.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Performance.measureUserAgentSpecificMemory()")}}