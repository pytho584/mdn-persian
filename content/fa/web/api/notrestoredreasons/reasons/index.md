---
title: "NotRestoredReasons: reasons property"
short-title: reasons
slug: Web/API/NotRestoredReasons/reasons
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasons.reasons
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`reasons`** در رابط {{domxref("NotRestoredReasons")}} آرایه‌ای از اشیاء {{domxref("NotRestoredReasonDetails")}} را بازمی‌گرداند که هر یک دلیلی را نشان می‌دهد که چرا صفحهٔ پیمایش‌شده از استفاده از حافظهٔ نهان عقب/جلو ({{Glossary("bfcache")}}) مسدود شده است.

## مقدار

آرایه‌ای از اشیاء {{domxref("NotRestoredReasonDetails")}}. برای فهرست دلایل مسدودسازی ممکن، [دلایل مسدودسازی](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons#blocking_reasons) را ببینید.

اگر سند در یک {{htmlelement("iframe")}} با مبدأ متقابل (cross-origin) قرار داشته باشد، `reasons` مقدار `null` را بازمی‌گرداند؛ با این حال، اگر هر یک از `<iframe>`ها استفاده از bfcache را برای فریم سطح بالا مسدود کرده باشند، سند والد ممکن است یک `reason` با مقدار `"masked"` نشان دهد.

## مثال‌ها

برای مثال‌ها، [پایش دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [پایش دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}