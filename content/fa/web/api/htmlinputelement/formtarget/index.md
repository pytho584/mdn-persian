---
title: "HTMLInputElement: formTarget property"
short-title: formTarget
slug: Web/API/HTMLInputElement/formTarget
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.formTarget
---

{{APIRef("HTML DOM")}}

خاصیت **`formTarget`** در رابط {{domxref("HTMLInputElement")}} مشخص‌کنندهٔ زبانه، پنجره یا iframeای است که پاسخ {{HtmlElement("form")}} ارسال‌شده در آن نمایش داده می‌شود. این مقدار منعکس‌کنندهٔ ویژگی [`formtarget`](/en-US/docs/Web/HTML/Reference/Elements/input#formtarget) عنصر {{HTMLElement("input")}} است.

این خاصیت فقط برای عناصر `<input>` از نوع [`submit`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است.

مقدار این خاصیت، خاصیت {{domxref("HTMLFormElement.target", "target")}} رابط {{domxref("HTMLFormElement")}} را در صورت ارسال فرم از طریق این ورودی، نادیده می‌گیرد. این خاصیت قابل خواندن و تنظیم است. در صورت تنظیم نبودن، مقدار آن رشتهٔ خالی (`""`) خواهد بود.

## مقدار

یک رشته.

## نمونه

```js
inputElement.formTarget = "_blank";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.formAction")}}
- {{domxref("HTMLInputElement.formEnctype")}}
- {{domxref("HTMLInputElement.formNoValidate")}}
- {{domxref("HTMLInputElement.formMethod")}}
- {{domxref("HTMLFormElement.target")}}
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image)
- [Sending form data](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)