---
title: "HTMLButtonElement: formEnctype property"
short-title: formEnctype
slug: Web/API/HTMLButtonElement/formEnctype
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.formEnctype
---

{{APIRef("HTML DOM")}}

ویژگی **`formEnctype`** در رابط {{domxref("HTMLButtonElement")}}، نوع {{Glossary("MIME_type", "MIME")}} محتوایی است که هنگام ارسال فرم به سرور فرستاده می‌شود. این ویژگی مقدار ویژگی [`formenctype`](/en-US/docs/Web/HTML/Reference/Elements/button#formenctype) عنصر `<button>` را بازتاب می‌دهد.

اگر فرم از طریق دکمه ارسال (submit) ارسال شود، این مقدار، ویژگی {{domxref("HTMLFormElement.enctype", "enctype")}} در رابط {{domxref("HTMLFormElement")}} را بازنویسی می‌کند. این ویژگی قابل خواندن و تنظیم است. اگر تنظیم نشده باشد، مقدار آن رشتهٔ خالی (`""`) است.

## مقدار

یک رشته.

## نمونه‌ها

```js
btnEl.formEnctype = "application/x-www-form-urlencoded";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLButtonElement.formAction")}}
- {{domxref("HTMLButtonElement.formMethod")}}
- {{domxref("HTMLButtonElement.formNoValidate")}}
- {{domxref("HTMLButtonElement.formTarget")}}
- {{domxref("HTMLFormElement.enctype")}}
- [ارسال داده‌های فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)
