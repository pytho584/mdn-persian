---
title: "HTMLInputElement: formNoValidate property"
short-title: formNoValidate
slug: Web/API/HTMLInputElement/formNoValidate
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.formNoValidate
---

{{APIRef("HTML DOM")}}

ویژگی **`formNoValidate`** در رابط {{domxref("HTMLInputElement")}} یک مقدار بولین است که نشان می‌دهد آیا {{htmlelement("form")}} هنگام ارسال از طریق {{htmlelement("input")}}، [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) را نادیده می‌گیرد یا خیر. این ویژگی، صفت [`formnovalidate`](/en-US/docs/Web/HTML/Reference/Elements/input#formnovalidate) عنصر `<input>` را بازتاب می‌دهد.

این ویژگی فقط برای عناصر `<input>` از نوع [`submit`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است.

اگر فرم از طریق این ورودی ارسال شود، مقدار این ویژگی، ویژگی {{domxref("HTMLFormElement.noValidate", "noValidate")}} در رابط {{domxref("HTMLFormElement")}} را نادیده می‌گیرد. این ویژگی قابل خواندن و تنظیم است.

## مقدار

یک مقدار بولین.

## مثال‌ها

```js
const inputElement = document.getElementById("myInput");
console.log(inputElement.formNoValidate);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.reportValidity()")}}
- {{domxref("HTMLInputElement.checkValidity()")}}
- {{domxref("HTMLInputElement.formAction")}}
- {{domxref("HTMLInputElement.formEnctype")}}
- {{domxref("HTMLInputElement.formMethod")}}
- {{domxref("HTMLInputElement.formTarget")}}
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image)
- {{HTMLElement("form")}}
- {{domxref("HTMLFormElement.noValidate")}}
- {{domxref("HTMLButtonElement.formNoValidate")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)