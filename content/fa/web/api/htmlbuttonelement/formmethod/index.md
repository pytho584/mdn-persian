---
title: "HTMLButtonElement: formMethod property"
short-title: formMethod
slug: Web/API/HTMLButtonElement/formMethod
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.formMethod
---

{{APIRef("HTML DOM")}}

ویژگی **`formMethod`** در رابط {{domxref("HTMLButtonElement")}}، متد {{Glossary("HTTP")}} است که برای ارسال {{HtmlElement("form")}} استفاده می‌شود، در صورتی که عنصر {{HTMLElement("button")}} کنترل ارسال فرم باشد. این ویژگی مقدار صفت [`formmethod`](/en-US/docs/Web/HTML/Reference/Elements/button#formmethod) عنصر `<button>` را بازتاب می‌دهد.

در صورت ارسال فرم از طریق دکمه، این مقدار ویژگی {{domxref("HTMLFormElement.method", "method")}} رابط {{domxref("HTMLFormElement")}} را بازنویسی می‌کند. این ویژگی قابل خواندن یا تنظیم شدن است. اگر با مقدار خالی یا نامعتبر تنظیم شود، مقدار پیش‌فرضِ مربوط به حالت نامعتبر `"get"` است. اگر اصلاً تنظیم نشده باشد، مقدار آن رشتهٔ خالی (`""`) است.

## Value

یک رشته؛ `"post"`، `"get"`، `"dialog"` یا `""`.

## Examples

```js
btnEl.formMethod = "post";
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLButtonElement.formAction")}}
- {{domxref("HTMLButtonElement.formEnctype")}}
- {{domxref("HTMLButtonElement.formNoValidate")}}
- {{domxref("HTMLButtonElement.formTarget")}}
- {{domxref("HTMLFormElement.method")}}
- [Sending form data](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)