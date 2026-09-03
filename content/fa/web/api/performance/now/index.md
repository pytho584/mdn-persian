---
title: "Performance: now() method"
---

---
title: "Performance: now() method"
short-title: now()
slug: Web/API/Performance/now
page-type: web-api-instance-method
browser-compat: api.Performance.now
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`performance.now()`** یک برچسب زمانی با دقت بالا را بر حسب میلی‌ثانیه برمی‌گرداند. این مقدار بیانگر زمان سپری‌شده از {{domxref("Performance.timeOrigin")}} است (زمانی که ناوبری در بافتارهای پنجره آغاز شده است، یا زمانی که کارگر (worker) در بافتارهای {{domxref("Worker")}} و {{domxref("ServiceWorker")}} اجرا می‌شود).

## نحو (Syntax)

```js-nolint
now()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("DOMHighResTimeStamp")}} را بر حسب میلی‌ثانیه برمی‌گرداند.

## توضیحات

### مقایسه `Performance.now` با `Date.now`

برخلاف [`Date.now`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/now)، برچسب‌های زمانی بازگردانده‌شده توسط `performance.now()` به دقت یک میلی‌ثانیه محدود نیستند. در عوض، آن‌ها زمان‌ها را به‌صورت اعداد اعشاری (floating-point) با دقت تا حد میکروثانیه نمایش می‌دهند.

همچنین، `Date.now()` ممکن است تحت تأثیر تنظیم ساعت توسط سیستم یا کاربر، انحراف ساعت (clock skew) و موارد مشابه قرار گیرد، زیرا نسبت به مبدأ یونیکس (1970-01-01T00:00:00Z) محاسبه می‌شود و به ساعت سیستم وابسته است. از سوی دیگر، متد `performance.now()` نسبت به خاصیت `timeOrigin` است که یک [ساعت یکنواخت (monotonic clock)](https://w3c.github.io/hr-time/#dfn-monotonic-clock) به شمار می‌رود: زمان جاری آن هرگز کاهش نمی‌یابد و در معرض تنظیم قرار نمی‌گیرد.

### تغییرات مشخصات `performance.now`

معناشناسی متد `performance.now()` بین سطح ۱ و سطح ۲ مشخصات High Resolution Time تغییر کرده است.

| تغییرات | سطح ۱ | سطح ۲ |
| --------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| نسبت به | [`performance.timing.navigationStart`](/en-US/docs/Web/API/PerformanceTiming/navigationStart) | {{domxref("Performance.timeOrigin")}} |
| شرایط فعال‌سازی | واکشی سند یا اعلان ترک صفحه (در صورت وجود). | ایجاد بافتار مرور (در صورت نبود سند قبلی)، اعلان ترک صفحه (در صورت وجود)، یا شروع ناوبری (طبق تعریف HTML، چند گام پیش از واکشی). |

متد `performance.now()` پیش‌تر نسبت به خاصیت [`performance.timing.navigationStart`](/en-US/docs/Web/API/PerformanceTiming/navigationStart) از مشخصات Navigation Timing بود. این رفتار تغییر کرده است و اکنون `performance.now()` نسبت به {{domxref("Performance.timeOrigin")}} است که هنگام مقایسه برچسب‌های زمانی بین صفحات وب، خطر تغییر ساعت را از میان برمی‌دارد.

```js
// Level 1 (clock change risks)
currentTime = performance.timing.navigationStart + performance.now();

// Level 2 (no clock change risks)
currentTime = performance.timeOrigin + performance.now();
```

### تیک زدن در هنگام خواب

مشخصات (سطح ۲) الزام می‌کند که `performance.now()` باید هنگام خواب رفتن سیستم‌عامل یا منجمد شدن فرایند مرورگر به هر شکل دیگری، به تیک زدن ادامه دهد. به نظر می‌رسد که تنها مرورگرهای ویندوز در طول خواب به تیک زدن ادامه می‌دهند. باگ‌های مربوط به مرورگرها در سایر سیستم‌عامل‌ها:

- Chrome/Chromium ([باگ](https://crbug.com/1206450))
- Firefox ([باگ](https://bugzil.la/1709767))
- Safari/WebKit ([باگ](https://webkit.org/b/225610))

بسته به مورد استفاده شما، این اختلاف ممکن است قابل توجه باشد یا نباشد. برای مثال، اگر زمان عملیات کوتاهی مانند بارگذاری یک تصویر را اندازه‌گیری می‌کنید (کاری که در آن مدت، خواب رفتن سیستم احتمال کمی دارد)، این موضوع ممکن است مشکلی ایجاد نکند. اگر زمان یک عملیات طولانی را اندازه‌گیری می‌کنید، ممکن است {{jsxref("Date.now()")}} را برای دور زدن این محدودیت‌ها مفیدتر بیابید، زیرا به هر حال دقت بالای `performance.now()` ممکن است چندان حیاتی نباشد.

جزئیات بیشتر را می‌توانید در بحث مربوط به مشخصات، [hr-time#115](https://github.com/w3c/hr-time/issues/115#issuecomment-1172985601)، بیابید.

## الزامات امنیتی

برای محافظت در برابر حملات زمان‌سنجی و [اثر انگشت دیجیتال (fingerprinting)](/en-US/docs/Glossary/Fingerprinting)، دقت `performance.now()` بر اساس اینکه سند {{domxref("Window.crossOriginIsolated","cross-origin isolated","","nocode")}} باشد یا نباشد، کاهش می‌یابد (coarsened).

- دقت در بافتارهای ایزوله‌شده: ۵ میکروثانیه
- دقت در بافتارهای غیرایزوله‌شده: ۱۰۰ میکروثانیه

برای بررسی اینکه آیا سند به‌صورت متقاطع-مبدأ ایزوله شده است، می‌توانید از خاصیت‌های {{domxref("Window.crossOriginIsolated")}} و {{domxref("WorkerGlobalScope.crossOriginIsolated")}} استفاده کنید:

```js
if (crossOriginIsolated) {
  // Use measureUserAgentSpecificMemory
}
```

## مثال‌ها

### استفاده از `performance.now()`

برای تعیین اینکه چه مقدار زمان از یک نقطه مشخص در کد شما سپری شده است، می‌توانید کاری شبیه به این انجام دهید:

```js
const t0 = performance.now();
doSomething();
const t1 = performance.now();
console.log(`Call to doSomething took ${t1 - t0} milliseconds.`);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("Performance.timeOrigin")}}