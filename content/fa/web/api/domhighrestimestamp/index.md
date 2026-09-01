---
title: "DOMHighResTimeStamp"
---

---
title: DOMHighResTimeStamp
slug: Web/API/DOMHighResTimeStamp
page-type: web-api-interface
spec-urls: https://w3c.github.io/hr-time/#dom-domhighrestimestamp
---

{{APIRef("Performance API")}}

**`DOMHighResTimeStamp`** یک نوع `double` است و برای ذخیره‌سازی یک مقدار زمانی بر حسب میلی‌ثانیه استفاده می‌شود.

این نوع می‌تواند برای توصیف یک نقطه زمانی مشخص یا یک بازه زمانی (تفاوت زمانی بین دو نقطه مشخص) به کار رود. زمان شروع می‌تواند یا یک زمان خاص باشد که توسط اسکریپت برای یک سایت یا برنامه تعیین شده است، یا [مبدأ زمان](/en-US/docs/Web/API/Performance/timeOrigin).

زمان بر حسب میلی‌ثانیه باید با دقت ۵ میکروثانیه (µs) باشد و بخش کسری عدد، کسری از میلی‌ثانیه را نشان دهد. با این حال، اگر مرورگر نتواند مقداری با دقت ۵ میکروثانیه ارائه دهد (مثلاً به دلیل محدودیت‌های سخت‌افزاری یا نرم‌افزاری)، می‌تواند مقدار را به‌صورت میلی‌ثانیه با دقت یک میلی‌ثانیه نمایش دهد. همچنین به بخش پایین‌تر درباره کاهش دقت زمان که توسط تنظیمات مرورگر کنترل می‌شود توجه کنید تا از حملات زمان‌بندی و [اثر انگشت دیجیتال](/en-US/docs/Glossary/Fingerprinting) جلوگیری شود.

علاوه بر این، اگر دستگاه یا سیستم عاملی که عامل کاربر روی آن اجرا می‌شود ساعتی با دقت میکروثانیه نداشته باشد، ممکن است دقت فقط در حد میلی‌ثانیه باشد.

## الزامات امنیتی

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت دیجیتال](/en-US/docs/Glossary/Fingerprinting)، انواع `DOMHighResTimeStamp` بر اساس وضعیت ایزوله‌سازی سایت، درشت‌دانه‌تر می‌شوند.

- دقت در زمینه‌های ایزوله: ۵ میکروثانیه
- دقت در زمینه‌های غیرایزوله: ۱۰۰ میکروثانیه

سایت خود را با استفاده از هدرهای {{HTTPHeader("Cross-Origin-Opener-Policy")}} و
{{HTTPHeader("Cross-Origin-Embedder-Policy")}} به‌صورت cross-origin ایزوله کنید:

```http
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp
```

این هدرها تضمین می‌کنند که یک سند سطح بالا گروه زمینه مرورگری را با اسناد cross-origin به اشتراک نمی‌گذارد. COOP سند شما را از نظر فرآیندی ایزوله می‌کند و مهاجمان احتمالی اگر سند شما را در یک پنجره بازشو باز کنند، به شیء سراسری شما دسترسی نخواهند داشت و از مجموعه‌ای از حملات cross-origin به نام [XS-Leaks](https://github.com/xsleaks/xsleaks) جلوگیری می‌کند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`performance.now()`](/en-US/docs/Web/API/Performance/now)
- [`performance.timeOrigin`](/en-US/docs/Web/API/Performance/timeOrigin)