---
title: CrashReportContext
slug: Web/API/CrashReportContext
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CrashReportContext
---

{{APIRef("Reporting API")}}{{SeeCompatTable}}

رابطِ `CrashReportContext` در [Reporting API](/en-US/docs/Web/API/Reporting_API) روش‌هایی را فراهم می‌کند که امکان ثبت داده‌های دلخواه برای «زمینهٔ مرور سطح بالا» فعلی را می‌دهند. این داده‌ها سپس به یک {{domxref("CrashReport")}} اضافه شده و در صورت بروز خرابی در مرورگر، به یک مقصد گزارش‌گیری ارسال می‌شوند.

برای دسترسی به شیء `CrashReportContext` مربوط به یک زمینهٔ مرور خاص، از ویژگی {{domxref("Window.crashReport")}} استفاده می‌شود.

## روش‌های نمونه

- {{domxref("CrashReportContext.delete()")}} {{experimental_inline}}
  - : یک جفت کلید-مقدار را که قبلاً ذخیره شده است حذف می‌کند.
- {{domxref("CrashReportContext.initialize()")}} {{experimental_inline}}
  - : بخشی از حافظه را برای ذخیره‌سازی داده‌های گزارش خرابی که توسط {{domxref("CrashReportContext.set", "set()")}} مشخص می‌شوند، مقداردهی اولیه می‌کند. این روش باید پیش از فراخوانی هر روش دیگری روی شیء فراخوانی شود.
- {{domxref("CrashReportContext.set()")}} {{experimental_inline}}
  - : یک جفت کلید-مقدار را در حافظه‌ای که توسط {{domxref("CrashReportContext.initialize", "initialize()")}} مقداردهی شده است ذخیره می‌کند.

## توضیحات

گزارش‌های خرابی حاوی اطلاعات دلخواه را می‌توان با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) به یک سرور مقصد ارسال کرد. این قابلیت مفید است، زیرا می‌توانیم اطلاعات تشخیصی دقیق را در طول عمر یک برنامه ذخیره کنیم و برای اشکال‌زدایی مؤثرتر خرابی‌ها از این گزارش‌ها استفاده کنیم.

اطلاعات در یک ذخیره‌گاه کلید-مقدار ویژه ذخیره می‌شود که مشابه [Web Storage](/en-US/docs/Web/API/Web_Storage_API) است، با این تفاوت که دامنهٔ آن به مبدأ سطح بالای فعلی محدود است و متد دریافت‌کننده نیز در دسترس ندارد. این امکان را می‌دهد که اطلاعات وضعیت مخصوص سند ثبت و حذف شوند. سند سطح بالا اطلاعات تشخیصی مربوط به خود و هر سند جاسازی‌شده را ثبت می‌کند و گزارش‌های خرابی مربوطه را ارسال می‌کند.

برای استفاده از این API، سند ابتدا باید {{domxref("CrashReportContext.initialize", "window.crashReport.initialize()")}} را فراخوانی کند. آرگومان این متد عددی است که حداکثر تعداد بایت‌هایی را مشخص می‌کند که هر فراخوانی جداگانهٔ {{domxref("CrashReportContext.set", "window.crashReport.set()")}} می‌تواند در ذخیره‌گاه کلید-مقدار ثبت کند. سپس مقادیر با استفاده از `set()` ثبت می‌شوند و با استفاده از {{domxref("CrashReportContext.delete", "window.crashReport.delete()")}} حذف می‌شوند.

هنگامی که مرورگر خراب می‌شود (crash)، اطلاعات ذخیره‌شده در ذخیره‌گاه کلید-مقدار به یک {{domxref("CrashReport")}} اضافه شده و به [مقصد پیش‌فرض سرور گزارش‌گیری](/en-US/docs/Web/HTTP/Reference/Headers/Reporting-Endpoints#default_reporting_endpoint) ارسال می‌شود.

> [!NOTE]
> امکان بازیابی {{domxref("CrashReport")}} با استفاده از {{domxref("ReportingObserver")}} وجود ندارد.

## نمونه‌ها

### ثبت داده در گزارش خرابی

برای شروع استفاده از گزارش‌گیری خرابی، یک برنامهٔ وب باید {{domxref("CrashReportContext.initialize", "window.crashReport.initialize()")}} را فراخوانی کند و حداکثر تعداد بایت‌هایی را تعیین کند که هر فراخوانی `set()` می‌تواند در ذخیره‌گاه کلید-مقدار ذخیره کند. در اینجا ذخیره‌گاه را با یک کیلوبایت فضای ذخیره‌سازی مقداردهی اولیه می‌کنیم:

```js
window.crashReport.initialize(1024).then(() => {
  init();
});
```

پس از اینکه پرامیس (Promise) به حالت resolved درآمد، چند راهبرد رایج وجود دارد که می‌توان در کدهای بعدی به کار گرفت. برای مثال، می‌توانیم یک جفت کلید-مقدار تنظیم کنیم که داده‌های ورودی یک عملیات پیچیده را که ممکن است باعث خرابی شود ذخیره کند و سپس آن عملیات را با این ورودی‌ها اجرا کنیم. اگر مرورگر خراب شود، {{domxref("CrashReport")}} حاصل آن داده‌ها را در بر خواهد داشت. اگر خراب نشد، می‌توانیم آن جفت کلید-مقدار را حذف کنیم، زیرا در آن لحظه به آن نیازی نداریم.

```js
const arg1 = "a";
const arg2 = "b";
window.crashReport.set("complex-operation-input", `${arg1}_${arg2}`);
complexOperationThatMightCrash(arg1, arg2);
window.crashReport.delete("complex-operation-input");
```

از آنجا که داده‌های ذخیره‌سازی خرابی در همهٔ اسناد هم‌مبدأ زیر یک مسیر پیمایشی (traversable navigable) قابل دسترسی هستند، ممکن است بخواهید برای برخی عملیات رایج که چند سند ممکن است هم‌زمان انجام دهند، پیشوندی به کلیدها اضافه کنید. برای مثال، فرض کنید یک عملیات معمول {{domxref("fetch()")}} در چندین سند مختلف در زمان‌های مختلف فراخوانی می‌شود و شرایط خاصی منجر به خرابی در این عملیات می‌شود.

برای کمک به شناسایی اینکه در زمان خرابی، `fetch()` از کجا فراخوانی شده است، می‌توانیم از راهبرد پیشوندگذاری استفاده کنیم:

```js
async function fetchURL(url) {
  const prefix = `[top-level=${self === window.top}]`;
  window.crashReport.set(`${prefix}-fetching`, url);
  const response = await fetch(url);
  window.crashReport.delete(`${prefix}-fetching`, url);
}
```

این کار همچنین از بازنویسی جفت‌های کلید-مقداری که یک مشکل یکسان را در زمان‌ها یا مکان‌های مختلف شناسایی می‌کنند، جلوگیری می‌کند. در این مورد، داده‌های گزارش خرابی ثبت‌شده در سند سطح بالا را از داده‌های ثبت‌شده در اسناد جاسازی‌شده متمایز می‌کنیم.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Reporting API](/en-US/docs/Web/API/Reporting_API)