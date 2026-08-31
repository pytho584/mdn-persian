---
title: "console: dir() static method"
short-title: dir()
slug: Web/API/console/dir_static
page-type: web-api-static-method
browser-compat: api.console.dir_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستا **`console.dir()`** فهرستی از ویژگی‌های شیء جاوااسکریپت مشخص‌شده را نمایش می‌دهد. در کنسول‌های مرورگر، خروجی به صورت فهرست سلسله‌مراتبی با مثلث‌های بازشونده ارائه می‌شود که به شما امکان می‌دهد محتویات اشیاء فرزند را مشاهده کنید.

برخلاف دیگر متدهای لاگ‌گیری، `console.dir()` تلاش نمی‌کند شیء را به صورت زیبا (pretty-print) نمایش دهد. برای مثال، اگر یک عنصر DOM را به `console.dir()` بدهید، مانند بازرس عنصر (element inspector) نمایش داده نمی‌شود، بلکه فهرستی از ویژگی‌ها را نشان می‌دهد.

![تصویری از کنسول فایرفاکس که در آن console.dir(document.location) اجرا شده است. URL صفحه را می‌بینیم و به دنبال آن بلوکی از ویژگی‌ها. اگر ویژگی یک تابع یا شیء باشد، یک مثلث بازشونده قبل از آن قرار دارد.](console-dir.png)

در زمان‌های اجرا (runtimes) مانند {{glossary("Node.js", "Node")}} و {{glossary("Deno")}}، که خروجی کنسول به ترمینال می‌رود و بنابراین تعاملی نیست، پارامتر `options` راهی برای سفارشی‌سازی نحوه ارائه شیء فراهم می‌کند.

## Syntax

```js-nolint
console.dir(object)
console.dir(object, options)
```

### Parameters

- `object`
  - : یک شیء جاوااسکریپت که ویژگی‌های آن باید چاپ شوند.
- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر، همه اختیاری:
    - `colors` {{non-standard_inline}} {{optional_inline}}
      - : یک مقدار بولی: اگر `true` باشد، ویژگی‌های شیء را بر اساس نوع آن‌ها سبک‌دهی می‌کند. پیش‌فرض `true`.
    - `depth` {{non-standard_inline}} {{optional_inline}}
      - : یک عدد که تعداد سطوح تو در تو را برای چاپ زمانی که یک شیء شامل اشیاء یا آرایه‌های دیگر است مشخص می‌کند. مقدار `null` به معنای چاپ همه سطوح است. پیش‌فرض ۲.
    - `showHidden` {{non-standard_inline}} {{optional_inline}}
      - : یک مقدار بولی: اگر `true` باشد، ویژگی‌های غیرقابل شمارش (non-enumerable) و نماد (symbol) شیء را چاپ می‌کند. پیش‌فرض `false`.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [مستندات Microsoft Edge برای `console.dir()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#dir)
- [مستندات Node.js برای `console.dir()`](https://nodejs.org/docs/latest/api/console.html#consoledirobj-options)
- [مستندات Google Chrome برای `console.dir()`](https://developer.chrome.com/docs/devtools/console/api/#dir)