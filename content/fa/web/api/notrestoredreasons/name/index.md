---
title: "NotRestoredReasons: name property"
---

---
title: "NotRestoredReasons: name property"
short-title: name
slug: Web/API/NotRestoredReasons/name
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasons.name
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`name`** از رابط {{domxref("NotRestoredReasons")}} یک رشته را برمی‌گرداند که مقدار ویژگی `name` عنصر {{htmlelement("iframe")}} حاوی سند را نشان می‌دهد (برای مثال `<iframe name="bar" src="...">`).

## مقدار

یک رشته.

اگر سند درون یک `<iframe>` نباشد یا `<iframe>` ویژگی `name` تنظیم شده نداشته باشد، `name` مقدار `null` را برمی‌گرداند.

## مثال‌ها

برای مثال‌ها به [نظارت بر دلایل مسدودسازی حافظه پنهان برگشت به عقب (bfcache)](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [نظارت بر دلایل مسدودسازی حافظه پنهان برگشت به عقب (bfcache)](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}