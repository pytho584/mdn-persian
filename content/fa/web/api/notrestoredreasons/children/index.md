---
title: "NotRestoredReasons: children property"
short-title: children
slug: Web/API/NotRestoredReasons/children
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasons.children
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`children`** از رابط {{domxref("NotRestoredReasons")}} آرایه‌ای از اشیاء {{domxref("NotRestoredReasons")}} برمی‌گرداند؛ یک شیء برای هر {{htmlelement("iframe")}} فرزندی که در سند فعلی جاسازی شده است. این اشیاء ممکن است شامل دلایل مسدود شدن فریم سطح بالا در رابطه با فریم‌های فرزند باشند.

هر شیء ساختاری مشابه شیء والد دارد؛ به این ترتیب، هر تعداد سطح از `<iframe>`های جاسازی‌شده می‌توانند به‌صورت بازگشتی در داخل شیء نمایش داده شوند.

## مقدار

آرایه‌ای از اشیاء {{domxref("NotRestoredReasons")}}.

اگر فریم فرزندی نداشته باشد، آرایه خالی خواهد بود؛ اگر سند در یک `<iframe>` متقاطع-ریشه (cross-origin) قرار داشته باشد، `children` مقدار `null` برمی‌گرداند.

## مثال‌ها

برای مثال‌ها، به [Monitoring bfcache blocking reasons](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Monitoring bfcache blocking reasons](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}