---
title: "console: time() static method"
---

---
title: "console: time() static method"
short-title: time()
slug: Web/API/console/time_static
page-type: web-api-static-method
browser-compat: api.console.time_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.time()`** یک زمان‌سنج را شروع می‌کند که می‌توانید برای پیگیری مدت‌زمان اجرای یک عملیات از آن استفاده کنید. به هر زمان‌سنج یک نام یکتا بدهید؛ در هر صفحه می‌توانید حداکثر ۱۰٬۰۰۰ زمان‌سنج فعال داشته باشید. وقتی با همان نام {{domxref("console/timeEnd_static", "console.timeEnd()")}} را فراخوانی کنید، مرورگر مدت‌زمان سپری‌شده از شروع زمان‌سنج را برحسب میلی‌ثانیه نمایش می‌دهد.

برای جزئیات و مثال‌ها، بخش [زمان‌سنج‌ها](/en-US/docs/Web/API/console#timers) را در مستندات {{domxref("console")}} ببینید.

## سینتکس

```js-nolint
console.time()
console.time(label)
```

### پارامترها

- `label` {{optional_inline}}
  - : رشته‌ای است که نام زمان‌سنج جدید را مشخص می‌کند. این نام، زمان‌سنج را شناسایی می‌کند؛ هنگام فراخوانی {{domxref("console/timeEnd_static", "console.timeEnd()")}} از همین نام استفاده کنید تا زمان‌سنج متوقف شود و مدت‌زمان سپری‌شده در کنسول نمایش داده شود. اگر این پارامتر حذف شود، برچسب `"default"` استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- برای مثال‌ها، {{domxref("console/timeLog_static", "console.timeLog()")}} و {{domxref("console/timeEnd_static", "console.timeEnd()")}} را ببینید
- [مستندات `console.time()` در Microsoft Edge](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#time)
- [مستندات `console.time()` در Node.js](https://nodejs.org/docs/latest/api/console.html#consoletimelabel)
- [مستندات `console.time()` در Google Chrome](https://developer.chrome.com/docs/devtools/console/api/#time)