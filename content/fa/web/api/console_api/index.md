---
title: Console API
slug: Web/API/Console_API
page-type: web-api-overview
browser-compat: api.console
---

{{DefaultAPISidebar("Console API")}} {{AvailableInWorkers}}

API کنسول (Console API) قابلیت‌هایی را در اختیار توسعه‌دهندگان قرار می‌دهد تا بتوانند کارهای اشکال‌زدایی را انجام دهند؛ مانند ثبت پیام‌ها یا مقادیر متغیرها در نقاط مشخصی از کد، یا اندازه‌گیری مدت زمانی که طول می‌کشد تا یک عملیات تکمیل شود.

## مفاهیم و کاربرد

API کنسول در ابتدا عمدتاً یک API اختصاصی بود و مرورگرهای مختلف آن را به شیوه‌های ناسازگار پیاده‌سازی می‌کردند. [مشخصات فنی API کنسول](https://console.spec.whatwg.org/) برای تعریف رفتار یکپارچه ایجاد شد و در نهایت همه مرورگرهای مدرن به پیاده‌سازی این رفتار روی آوردند؛ اگرچه برخی پیاده‌سازی‌ها همچنان توابع اختصاصی اضافی خود را دارند. این موارد را در این نشانی‌ها ببینید:

- [پیاده‌سازی Google Chrome DevTools](https://developer.chrome.com/docs/devtools/console/api/)
- [پیاده‌سازی Safari DevTools](https://webkit.org/web-inspector/console-object-api/)

استفاده از آن بسیار ساده است — شیء {{domxref("console")}} شامل متدهای زیادی است که می‌توانید برای انجام کارهای ابتدایی اشکال‌زدایی صدا بزنید؛ این متدها عمدتاً بر ثبت مقادیر مختلف در [کنسول وب](https://firefox-source-docs.mozilla.org/devtools-user/web_console/index.html) مرورگر متمرکز هستند.

بدون شک پرکاربردترین متد، {{domxref("console/log_static", "console.log()")}} است که برای ثبت مقدار فعلیِ درونِ یک متغیر خاص به کار می‌رود.

## رابط‌ها

- {{domxref("console")}}
  - : قابلیت‌های ابتدایی اشکال‌زدایی، شامل ثبت لاگ، ردیابی پشته، زمان‌سنج‌ها و شمارنده‌ها را فراهم می‌کند.

## مثال‌ها

```js
let myString = "Hello world";

// Output "Hello world" to the console
console.log(myString);
```

برای مثال‌های بیشتر به صفحه مرجع [console](/en-US/docs/Web/API/console) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ابزارها](https://firefox-source-docs.mozilla.org/devtools-user/index.html)
- [کنسول وب](https://firefox-source-docs.mozilla.org/devtools-user/web_console/index.html) — نحوه مدیریت فراخوانی‌های API کنسول در کنسول وب فایرفاکس
- [about:debugging](https://firefox-source-docs.mozilla.org/devtools-user/about_colon_debugging/index.html) — نحوه مشاهده خروجی کنسول وقتی هدف اشکال‌زدایی یک دستگاه همراه است.