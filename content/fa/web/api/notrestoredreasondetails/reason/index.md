---
title: "NotRestoredReasonDetails: reason property"
short-title: reason
slug: Web/API/NotRestoredReasonDetails/reason
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasonDetails.reason
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط-خواندنی **`reason`** از رابط {{domxref("NotRestoredReasonDetails")}} یک رشته (string) برمی‌گرداند که دلیلی را توصیف می‌کند که باعث شده صفحه از استفاده از حافظه نهان جلو/عقب ({{Glossary("bfcache")}}) مسدود شود.

## مقدار

یک رشته (string).

دلایل مختلفی برای وقوع مسدودیت وجود دارد و مرورگرها می‌توانند دلایل خاص خود را بر اساس نحوه عملکردشان پیاده‌سازی کنند. توسعه‌دهندگان باید از وابسته شدن به عبارت‌های خاص برای دلایل خودداری کرده و آماده مدیریت دلایل جدیدی باشند که اضافه یا حذف می‌شوند.

مقادیر اولیه ذکر شده در مشخصات (specification) عبارتند از:

- `"fetch"`
  - : در حین تخلیه (unloading)، یک درخواست fetch که توسط سند جاری آغاز شده بود (مثلاً از طریق {{domxref("Window/fetch", "fetch()")}}) در حالی که هنوز در جریان بود لغو شد. در نتیجه، صفحه در وضعیت پایداری نبود که بتواند در bfcache ذخیره شود.
- `"lock"`
  - : در حین تخلیه، قفل‌های نگه‌داشته شده و درخواست‌های قفل خاتمه یافتند، بنابراین صفحه در وضعیت پایداری نبود که بتواند در bfcache ذخیره شود.
- `"masked"`
  - : دلیل دقیق به دلایل حریم خصوصی پنهان شده است. این مقدار می‌تواند یکی از موارد زیر را معنی دهد:
    - سند جاری دارای فرزندانی (children) در یک {{htmlelement("iframe")}} با مبدأ متفاوت (cross-origin) است و آن‌ها از ذخیره‌سازی در bfcache جلوگیری کرده‌اند.
    - سند (Document) جاری به دلایل خاص عامل کاربر (user agent) نتوانسته در bfcache ذخیره شود.
- `"navigation-failure"`
  - : پیمایش اصلی (original navigation) که سند جاری را ایجاد کرد با خطا مواجه شد و ذخیره سند خطای حاصل در bfcache مسدود شد.
- `"parser-aborted"`
  - : سند جاری هرگز تجزیه (parsing) اولیه HTML خود را به پایان نرساند و ذخیره سند ناقص در bfcache مسدود شد.
- `"websocket"`
  - : در حین تخلیه، یک اتصال [WebSocket](/en-US/docs/Web/API/WebSockets_API) باز بسته شد، بنابراین صفحه در وضعیت پایداری نبود که بتواند در bfcache ذخیره شود.

دلایل مسدودیت اضافی ممکن است توسط برخی مرورگرها استفاده شود، به عنوان مثال:

- `"unload-listener"`
  - : صفحه یک مدیریت‌کننده (handler) برای رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) ثبت کرده است که از استفاده از bfcache جلوگیری می‌کند. این یک هشدار مفید است زیرا `unload` منسوخ (deprecated) شده است. برای اطلاعات بیشتر به [یادداشت‌های استفاده](/en-US/docs/Web/API/Window/unload_event#usage_notes) مراجعه کنید.
- `"response-cache-control-no-store"`
  - : صفحه از `no-store` به عنوان مقدار هدر {{httpheader("Cache-Control")}} استفاده می‌کند.
- `"related-active-contents"`
  - : صفحه از صفحه دیگری باز شده است که هنوز یک ارجاع (reference) به این صفحه دارد، برای مثال با استفاده از قابلیت «تب تکراری» (duplicate tab).

## مثال‌ها

برای مثال‌ها به [نظارت بر دلایل مسدودیت bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نظارت بر دلایل مسدودیت bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}