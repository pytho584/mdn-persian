---
title: "console: warn() static method"
---

---
title: "console: warn() static method"
short-title: warn()
slug: Web/API/console/warn_static
page-type: web-api-static-method
browser-compat: api.console.warn_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.warn()`** یک پیام هشدار را در سطح لاگ «هشدار» به کنسول خروجی می‌دهد. این پیام فقط در صورتی به کاربر نمایش داده می‌شود که کنسول برای نمایش خروجی هشدار پیکربندی شده باشد. در بیشتر موارد، سطح لاگ در رابط کاربری کنسول پیکربندی می‌شود. ممکن است پیام قالب‌بندی خاصی مانند رنگ زرد و یک آیکن هشدار دریافت کند.

## Syntax

```js-nolint
console.warn(val1)
console.warn(val1, /* …, */ valN)
console.warn(msg)
console.warn(msg, subst1, /* …, */ substN)
```

### Parameters

- `val1` … `valN`
  - : فهرستی از مقادیر جاوااسکریپت برای خروجی. نمایشی از هر یک از این مقادیر به ترتیب داده‌شده با نوعی جداسازی بین هر یک از آن‌ها به کنسول خروجی داده می‌شود. اگر `val1` یک رشته باشد، حالت خاصی وجود دارد که در ادامه توضیح داده شده است.
- `msg`
  - : یک رشته جاوااسکریپت شامل صفر یا چند رشته جایگزینی که به ترتیب پیاپی تا تعداد رشته‌های جایگزینی با `subst1` تا `substN` جایگزین می‌شوند. برای توضیح نحوه کار جایگزینی‌ها، [استفاده از جایگزینی رشته‌ها](/en-US/docs/Web/API/console#using_string_substitutions) را ببینید.
- `subst1` … `substN`
  - : مقادیر جاوااسکریپت که با آن‌ها رشته‌های جایگزینی درون `msg` جایگزین می‌شوند. اگر تعداد مقادیر جایگزینی بیشتر از تعداد رشته‌های جایگزینی باشد، مقادیر اضافی به همان شکلی که وقتی رشته قالبی وجود ندارد، پس از پیام اعلان جزئیات به کنسول نوشته می‌شوند.

برای جزئیات بیشتر، [خروجی متن به کنسول](/en-US/docs/Web/API/console#outputting_text_to_the_console) را در مستندات {{domxref("console")}} ببینید.

### Return value

هیچ ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [مستندات Microsoft Edge برای `console.warn()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#warn)
- [مستندات Node.js برای `console.warn()`](https://nodejs.org/docs/latest/api/console.html#consolewarndata-args)
- [مستندات Google Chrome برای `console.warn()`](https://developer.chrome.com/docs/devtools/console/api/#warn)