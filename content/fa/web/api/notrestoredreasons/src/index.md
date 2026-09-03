---
title: "NotRestoredReasons: src property"
short-title: src
slug: Web/API/NotRestoredReasons/src
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasons.src
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`src`** از رابط {{domxref("NotRestoredReasons")}} یک رشته را برمی‌گرداند که مسیر منبع {{htmlelement("iframe")}}ای که سند در آن قرار دارد را نشان می‌دهد (برای مثال `<iframe src="b.html">`).

## مقدار

یک رشته.

اگر سند در یک `<iframe>` نباشد، `src` مقدار `null` را برمی‌گرداند.

## مثال‌ها

برای مثال‌ها به [نظارت بر دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نظارت بر دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}