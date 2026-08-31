---
title: "console: log() static method"
short-title: log()
slug: Web/API/console/log_static
page-type: web-api-static-method
browser-compat: api.console.log_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.log()`** یک پیام را در کنسول نمایش می‌دهد.

## نحو (Syntax)

```js-nolint
console.log(val1)
console.log(val1, /* …, */ valN)
console.log(msg)
console.log(msg, subst1, /* …, */ substN)
```

### پارامترها

- `val1` … `valN`
  - : فهرستی از مقادیر جاوااسکریپت برای نمایش. نمایش هر یک از این مقادیر به ترتیب ذکر شده و با نوعی جداکننده بین آن‌ها در کنسول چاپ می‌شود. یک حالت خاص وجود دارد اگر `val1` یک رشته باشد، که در ادامه توضیح داده شده است.
- `msg`
  - : یک رشته جاوااسکریپت حاوی صفر یا چند رشتهٔ جایگزین که با مقادیر `subst1` تا `substN` به ترتیب و تا تعداد رشته‌های جایگزین تعویض می‌شوند. برای توضیح نحوهٔ عملکرد جایگزینی، به [استفاده از جایگزینی رشته‌ها](/en-US/docs/Web/API/console#using_string_substitutions) مراجعه کنید.
- `subst1` … `substN`
  - : مقادیر جاوااسکریپت برای جایگزینی رشته‌های جایگزین درون `msg`. اگر تعداد مقادیر جایگزین بیشتر از رشته‌های جایگزین باشد، مقادیر اضافی پس از پیام تأکیدی دقیق به همان صورت که در صورت عدم وجود رشتهٔ قالب وجود دارد، در کنسول نوشته می‌شوند.

برای جزئیات بیشتر به [خروجی متن به کنسول](/en-US/docs/Web/API/console#outputting_text_to_the_console) در مستندات {{domxref("console")}} مراجعه کنید.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.log()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#log)
- [مستندات Node.js برای `console.log()`](https://nodejs.org/docs/latest/api/console.html#consolelogdata-args)
- [مستندات Google Chrome برای `console.log()`](https://developer.chrome.com/docs/devtools/console/api/#log)