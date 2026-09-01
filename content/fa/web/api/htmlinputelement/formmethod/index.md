---
title: "HTMLInputElement: formMethod property"
short-title: formMethod
slug: Web/API/HTMLInputElement/formMethod
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.formMethod
---

{{APIRef("HTML DOM")}}

خاصیت **`formMethod`** از رابط {{domxref("HTMLInputElement")}}، روش {{Glossary("HTTP")}} است که برای ارسال {{HtmlElement("form")}} استفاده می‌شود، در صورتی که عنصر {{HTMLElement("input")}} کنترلی باشد که فرم را ارسال می‌کند. این خاصیت مقدار ویژگی [`formmethod`](/en-US/docs/Web/HTML/Reference/Elements/input#formmethod) عنصر `<input>` را منعکس می‌کند.

این خاصیت فقط برای عناصر `<input>` از نوع [`submit`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است.

این مقدار، خاصیت {{domxref("HTMLFormElement.method", "method")}} از رابط {{domxref("HTMLFormElement")}} را در صورت ارسال فرم از طریق input جایگزین می‌کند. این خاصیت قابل دریافت یا تنظیم است. اگر با مقدار خالی یا نامعتبر تنظیم شود، مقدار پیش‌فرض نامعتبر `"get"` است. اگر اصلاً تنظیم نشود، مقدار آن رشته خالی (`""`) است.

## مقدار

یک رشته؛ `"post"`، `"get"`، `"dialog"`، یا `""`.

## مثال‌ها

```js
inputElement.formMethod = "post";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.formAction")}}
- {{domxref("HTMLInputElement.formEnctype")}}
- {{domxref("HTMLInputElement.formNoValidate")}}
- {{domxref("HTMLInputElement.formTarget")}}
- {{domxref("HTMLFormElement.method")}}
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image)
- [Sending form data](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)