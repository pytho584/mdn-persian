---
title: "Document: currentScript property"
short-title: currentScript
slug: Web/API/Document/currentScript
page-type: web-api-instance-property
browser-compat: api.Document.currentScript
---

{{APIRef("DOM")}}

خاصیت **`Document.currentScript`** عنصر {{HTMLElement("script")}}ای را برمی‌گرداند که اسکریپت آن در حال پردازش است و [یک ماژول جاوااسکریپت نیست](https://github.com/whatwg/html/issues/997). (برای ماژول‌ها به جای آن از [`import.meta`](/en-US/docs/Web/JavaScript/Reference/Operators/import.meta) استفاده کنید.)

توجه به این نکته مهم است که اگر کد موجود در اسکریپت به عنوان یک callback یا کنترل‌کننده رویداد فراخوانی شود، این خاصیت به عنصر {{HTMLElement("script")}} اشاره نخواهد کرد؛ بلکه فقط در زمانی که اسکریپت به صورت اولیه در حال پردازش است به آن عنصر اشاره می‌کند.

## مقدار

یک {{domxref("HTMLScriptElement")}} یا null.

## مثال‌ها

این مثال بررسی می‌کند که آیا اسکریپت به صورت ناهمگام (async) اجرا می‌شود یا خیر:

```js
if (document.currentScript.async) {
  console.log("Executing asynchronously");
} else {
  console.log("Executing synchronously");
}
```

[مشاهده نمونه‌های زنده](https://mdn.dev/archives/media/samples/html/currentScript.html)

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [`import.meta`](/en-US/docs/Web/JavaScript/Reference/Operators/import.meta)
- {{HTMLElement("script")}}
- رویداد {{DOMxRef("document.afterscriptexecute_event", "afterscriptexecute")}} از `Document`
- رویداد {{DOMxRef("document.beforescriptexecute_event", "beforescriptexecute")}} از `Document`