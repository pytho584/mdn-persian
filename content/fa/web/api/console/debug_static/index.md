---
title: "console: debug() static method"
short-title: debug()
slug: Web/API/console/debug_static
page-type: web-api-static-method
browser-compat: api.console.debug_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد استاتیک **`console.debug()`** یک پیام را در سطح ثبت «debug» به کنسول خروجی می‌دهد. این پیام تنها زمانی به کاربر نمایش داده می‌شود که کنسول برای نمایش خروجی debug پیکربندی شده باشد. در بیشتر موارد، سطح ثبت از طریق رابط کاربری کنسول پیکربندی می‌شود. این سطح ثبت ممکن است با سطح ثبت `Debug` یا `Verbose` مطابقت داشته باشد.

## نحو

```js-nolint
console.debug(val1)
console.debug(val1, /* …, */ valN)
console.debug(msg)
console.debug(msg, subst1, /* …, */ substN)
```

### پارامترها

- `val1` … `valN`
  - : فهرستی از مقادیر جاوااسکریپت برای خروجی. نمایشی از هر یک از این مقادیر به ترتیب داده شده با نوعی جداسازی بین هر یک از آنها به کنسول خروجی داده می‌شود. یک حالت خاص وجود دارد اگر `val1` یک رشته باشد، که در ادامه توضیح داده شده است.
- `msg`
  - : یک رشته جاوااسکریپت حاوی صفر یا چند رشته جایگزین که به ترتیب متوالی با `subst1` تا `substN` تا تعداد رشته‌های جایگزین جایگزین می‌شوند. برای توضیح نحوه کار جایگزینی‌ها به [استفاده از جایگزینی رشته‌ها](/en-US/docs/Web/API/console#using_string_substitutions) مراجعه کنید.
- `subst1` … `substN`
  - : مقادیر جاوااسکریپت که برای جایگزینی رشته‌های جایگزین درون `msg` استفاده می‌شوند. اگر تعداد مقادیر جایگزین بیشتر از تعداد رشته‌های جایگزین باشد، مقادیر اضافی خودشان پس از پیام اظهار دقیق به همان روشی که وقتی رشته قالب وجود ندارد، به کنسول نوشته می‌شوند.

برای جزئیات بیشتر، [خروجی متن به کنسول](/en-US/docs/Web/API/console#outputting_text_to_the_console) را در مستندات {{domxref("console")}} ببینید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.debug()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#debug)
- [مستندات Node.js برای `console.debug()`](https://nodejs.org/docs/latest/api/console.html#consoledebugdata-args)
- [مستندات Google Chrome برای `console.debug()`](https://developer.chrome.com/docs/devtools/console/api/#debug)