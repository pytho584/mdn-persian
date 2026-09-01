---
title: "HTMLInputElement: formEnctype property"
short-title: formEnctype
slug: Web/API/HTMLInputElement/formEnctype
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.formEnctype
---

{{APIRef("HTML DOM")}}

خاصیت **`formEnctype`** در رابط {{domxref("HTMLInputElement")}}، نوع {{Glossary("MIME_type", "MIME")}} محتوایی است که هنگام ارسال فرم با استفاده از `<input>` دارای ویژگی `formEnctype` به سرور فرستاده می‌شود. این خاصیت مقدار ویژگی [`formenctype`](/en-US/docs/Web/HTML/Reference/Elements/input#formenctype) عنصر `<input>` را منعکس می‌کند.

این خاصیت فقط برای عناصر `<input>` از نوع [`submit`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است.

اگر فرم از طریق این input ارسال شود، مقدار این خاصیت، خاصیت {{domxref("HTMLFormElement.enctype", "enctype")}} را در رابط {{domxref("HTMLFormElement")}} بازنویسی می‌کند. این خاصیت قابل خواندن و نوشتن است. اگر تنظیم نشده باشد، مقدار آن رشتهٔ خالی (`""`) خواهد بود.

## مقدار

یک رشته (string).

## مثال‌ها

```js
inputElement.formEnctype = "application/x-www-form-urlencoded";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.formAction")}}
- {{domxref("HTMLInputElement.formMethod")}}
- {{domxref("HTMLInputElement.formNoValidate")}}
- {{domxref("HTMLInputElement.formTarget")}}
- {{domxref("HTMLFormElement.enctype")}}
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image)
- [ارسال داده‌های فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)