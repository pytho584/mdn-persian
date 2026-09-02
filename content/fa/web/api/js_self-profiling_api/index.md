---
title: "JS Self-Profiling API"
---

---
title: JS Self-Profiling API
slug: Web/API/JS_Self-Profiling_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.Profiler
spec-urls: https://wicg.github.io/js-self-profiling/
---

{{DefaultAPISidebar("JS Self-Profiling API")}}{{SeeCompatTable}}

API JS Self-Profiling به وب‌سایت‌ها امکان می‌دهد تا یک پروفایل‌ساز نمونه‌بردار (sampling profiler) اجرا کنند و بفهمند زمان اجرای JavaScript در کجا صرف می‌شود.

## مفاهیم و کاربرد

برای شروع یک پروفایل، وب‌سایت یک نمونه از {{domxref("Profiler")}} می‌سازد. به محض ایجاد نمونه، نمونه‌برداری از زمینه اجرای JavaScript آغاز می‌شود.

برای توقف جمع‌آوری نمونه‌ها و دریافت پروفایل، وب‌سایت متد {{domxref("Profiler.stop()")}} را فراخوانی می‌کند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که به یک شی حاوی داده‌های پروفایل تبدیل می‌شود.

برای مثال، تابع زیر یک پروفایل‌ساز می‌سازد، سپس تابع `genPrimes()` را فراخوانی می‌کند، سپس پروفایل‌ساز را متوقف کرده و داده‌های پروفایل را دریافت می‌کند:

```js
async function profileGeneratePrimes() {
  const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 10000 });

  genPrimes();

  const trace = await profiler.stop();
  console.log(trace);
}
```

پروفایل‌ساز یک _پروفایل‌ساز نمونه‌بردار (sampling profiler)_ است: یعنی به‌طور دوره‌ای وضعیت فعلی {{glossary("call stack", "پشته‌ی فراخوانی")}} JavaScript را ثبت (یا _نمونه‌برداری_) می‌کند. پروفایل شامل مجموعه‌ای از این نمونه‌هاست. این به شما امکان می‌دهد بفهمید برنامه به‌طور آماری بیشترین زمان خود را کجا صرف می‌کند.

برای درک دقیق محتوای یک پروفایل و قالب‌بندی آن، به [ساختار و قالب پروفایل](/en-US/docs/Web/API/JS_Self-Profiling_API/Profile_content_and_format) مراجعه کنید.

### بهترین روش‌های پروفایل‌گیری

جمع‌آوری و پردازش داده‌های پروفایل خود هزینه‌ای بر عملکرد سیستم تحمیل می‌کند و توسعه‌دهندگان باید مراقب مدیریت آن باشند. روش‌های کاهش این هزینه عبارتند از:

- استفاده از گزینه‌های [`maxBufferSize`](/en-US/docs/Web/API/Profiler/Profiler#maxbuffersize) و [`sampleInterval`](/en-US/docs/Web/API/Profiler/Profiler#sampleinterval) برای کنترل تعداد نمونه‌ها و فاصله‌ی نمونه‌برداری.
- نمونه‌برداری برای مدت‌های کوتاه به‌صورت نمونه‌ای: مثلاً به‌مدت ۵ ثانیه از هر ۶۰ ثانیه ردیابی کنید.
- پردازش نمونه‌ها در یک web worker برای جلوگیری از تأثیر بر عملکرد نخ اصلی.
- تجمیع نمونه‌ها در سمت کاربر قبل از ارسال به یک نقطه‌ی پایانی (endpoint) تله‌متری.

اگر JavaScript وب‌سایت شما {{glossary("Minification", "فشرده (minified)")}} شده باشد، باید داده‌های پروفایل را بر اساس {{glossary("Source map", "نقشه‌ی منبع (source map)")}} تبدیل کنید، چه در سمت کاربر و چه در سمت سرور، تا داده‌ها قابل استفاده شوند.

## رابط‌ها

- {{domxref("Profiler")}} {{Experimental_Inline}}
  - رابط `Profiler` برای ایجاد پروفایل‌ها استفاده می‌شود.

## الزامات امنیتی

برای استفاده از این API، سند باید با یک [خط‌مشی سند (document policy)](https://wicg.github.io/document-policy/) که شامل نقطه‌ی پیکربندی `"js-profiling"` است، ارائه شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}