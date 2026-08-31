---
title: "console: info() static method"
short-title: info()
slug: Web/API/console/info_static
page-type: web-api-static-method
browser-compat: api.console.info_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.info()`** یک پیام را در سطح گزارش «info» در کنسول خروجی می‌دهد. پیام تنها در صورتی به کاربر نمایش داده می‌شود که کنسول برای نمایش خروجی‌های سطح info پیکربندی شده باشد. در بیشتر موارد، سطح گزارش در رابط کاربری کنسول تنظیم می‌شود. ممکن است این پیام قالب‌بندی خاصی دریافت کند، مانند یک آیکون کوچک «i» در کنار آن.

## Syntax

```js-nolint
console.info(val1)
console.info(val1, /* …, */ valN)
console.info(msg)
console.info(msg, subst1, /* …, */ substN)
```

### Parameters

- `val1` … `valN`
  - : فهرستی از مقادیر جاوااسکریپت برای خروجی دادن. نمایش هر یک از این مقادیر به ترتیب داده‌شده و با نوعی جداسازی بین آن‌ها در کنسول خروجی داده می‌شود. یک حالت خاص زمانی وجود دارد که `val1` یک رشته باشد که در ادامه توضیح داده شده است.
- `msg`
  - : یک رشته جاوااسکریپت شامل صفر یا چند رشته جایگزین (substitution string) که به ترتیب و تا تعداد رشته‌های جایگزین، با `subst1` تا `substN` جایگزین می‌شوند. برای توضیح نحوه کار جایگزینی‌ها، به [استفاده از جایگزینی رشته‌ها](/en-US/docs/Web/API/console#using_string_substitutions) مراجعه کنید.
- `subst1` … `substN`
  - : مقادیر جاوااسکریپتی که رشته‌های جایگزین درون `msg` با آن‌ها جایگزین می‌شوند. اگر تعداد مقادیر جایگزین بیشتر از تعداد رشته‌های جایگزین باشد، مقادیر اضافی به همان شکلی که وقتی رشته قالبی وجود ندارد، پس از پیام تأیید جزئی در کنسول نوشته می‌شوند.

برای جزئیات بیشتر به [خروجی متن به کنسول](/en-US/docs/Web/API/console#outputting_text_to_the_console) در مستندات {{domxref("console")}} مراجعه کنید.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [مستندات مایکروسافت اج برای `console.info()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#info)
- [مستندات Node.js برای `console.info()`](https://nodejs.org/docs/latest/api/console.html#consoleinfodata-args)
- [مستندات گوگل کروم برای `console.info()`](https://developer.chrome.com/docs/devtools/console/api/#info)