---
title: NotRestoredReasonDetails
slug: Web/API/NotRestoredReasonDetails
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NotRestoredReasonDetails
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

رابط **`NotRestoredReasonDetails`** از {{domxref("Performance API", "Performance API", "", "nocode")}} یک دلیل خاص برای مسدود شدن یک صفحهٔ مرور شده از استفاده از حافظهٔ نهان بازگشت/پیشرو ({{Glossary("bfcache")}}) را نشان می‌دهد.

یک آرایه از اشیاء `NotRestoredReasonDetails` از طریق ویژگی {{domxref("NotRestoredReasons.reasons")}} قابل دسترسی است.

## ویژگی‌های نمونه

- {{domxref("NotRestoredReasonDetails.reason", "reason")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته که دلیلی را توصیف می‌کند که صفحه از استفاده از حافظهٔ نهان بازگشت/پیشرو مسدود شده است.

## روش‌های نمونه

- {{domxref("NotRestoredReasonDetails.toJSON", "toJSON()")}} {{Experimental_Inline}}
  - : یک {{Glossary("Serialization","سریال‌کننده")}}؛ یک نمایش JSON از شیء `NotRestoredReasonDetails` بازمی‌گرداند.

## مثال‌ها

برای مثال‌ها به [نظارت بر دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نظارت بر دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}