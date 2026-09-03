---
title: "NotRestoredReasons: id property"
short-title: id
slug: Web/API/NotRestoredReasons/id
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasons.id
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`id`** از رابط {{domxref("NotRestoredReasons")}} یک رشته برمی‌گرداند که مقدار ویژگی `id` عنصر {{htmlelement("iframe")}} حاوی سند را نشان می‌دهد (مثلاً `<iframe id="foo" src="...">`).

## مقدار

یک رشته.

اگر سند درون یک `<iframe>` نباشد یا `<iframe>` ویژگی `id` تنظیم‌شده‌ای نداشته باشد، `id` مقدار `null` را برمی‌گرداند.

## مثال‌ها

برای مشاهده مثال‌ها به [نظارت بر دلایل مسدودسازی حافظه نهان bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نظارت بر دلایل مسدودسازی حافظه نهان bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}