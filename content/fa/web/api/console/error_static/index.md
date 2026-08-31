---
title: "console: error() static method"
short-title: error()
slug: Web/API/console/error_static
page-type: web-api-static-method
browser-compat: api.console.error_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.error()`** یک پیام را در سطح لاگ «error» به کنسول خروجی می‌دهد. پیام تنها در صورتی به کاربر نمایش داده می‌شود که کنسول برای نمایش خروجی خطا پیکربندی شده باشد. در بیشتر موارد، سطح لاگ درون رابط کاربری کنسول پیکربندی می‌شود. ممکن است پیام به صورت یک خطا، با رنگ قرمز و اطلاعات پشته فراخوانی قالب‌بندی شود.

## Syntax

```js-nolint
console.error(val1)
console.error(val1, /* …, */ valN)
console.error(msg)
console.error(msg, subst1, /* …, */ substN)
```

### پارامترها

- `val1` … `valN`
  - : فهرستی از مقادیر JavaScript برای خروجی. نمایشی از هر یک از این مقادیر به ترتیب با نوعی جداکننده بین آن‌ها به کنسول خروجی داده می‌شود. یک حالت خاص وجود دارد اگر `val1` یک رشته باشد که در ادامه توضیح داده شده است.
- `msg`
  - : یک رشته JavaScript شامل صفر یا چند رشته جایگزین که با مقادیر `subst1` تا `substN` به ترتیب و تا تعداد رشته‌های جایگزین تعویض می‌شوند. برای توضیح نحوه کار جایگزینی به [استفاده از جایگزینی رشته‌ها](/en-US/docs/Web/API/console#using_string_substitutions) مراجعه کنید.
- `subst1` … `substN`
  - : مقادیر JavaScript که برای جایگزینی رشته‌های جایگزین درون `msg` استفاده می‌شوند. اگر تعداد مقادیر جایگزین بیشتر از رشته‌های جایگزین باشد، مقادیر اضافی خودشان پس از پیام تفصیلی تأیید به همان روشی که در صورت عدم وجود رشته قالب وجود دارد، به کنسول نوشته می‌شوند.

برای جزئیات بیشتر، [خروجی متن به کنسول](/en-US/docs/Web/API/console#outputting_text_to_the_console) را در مستندات {{domxref("console")}} ببینید.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.error()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#error)
- [مستندات Node.js برای `console.error()`](https://nodejs.org/docs/latest/api/console.html#consoleerrordata-args)
- [مستندات Google Chrome برای `console.error()`](https://developer.chrome.com/docs/devtools/console/api/#error)