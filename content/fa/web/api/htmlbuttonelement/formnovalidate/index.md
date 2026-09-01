---
title: "HTMLButtonElement: formNoValidate property"
short-title: formNoValidate
slug: Web/API/HTMLButtonElement/formNoValidate
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.formNoValidate
---

{{APIRef("HTML DOM")}}

ویژگی **`formNoValidate`** در رابط {{domxref("HTMLButtonElement")}} یک مقدار بولی است که نشان می‌دهد آیا {{htmlelement("form")}} هنگام ارسال از طریق {{htmlelement("button")}}، [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) را نادیده می‌گیرد یا خیر. این ویژگی بازتابی از ویژگی [`formnovalidate`](/en-US/docs/Web/HTML/Reference/Elements/button#formnovalidate) عنصر `<button>` است.

مقدار این ویژگی، اگر فرم از طریق دکمه ارسال شود، بر ویژگی {{domxref("HTMLFormElement.noValidate", "noValidate")}} در رابط {{domxref("HTMLFormElement")}} غلبه می‌کند. این ویژگی قابل خواندن و تنظیم است.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const buttonElement = document.getElementById("myButton");
console.log(buttonElement.formNoValidate);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLButtonElement.reportValidity()")}}
- {{domxref("HTMLButtonElement.checkValidity()")}}
- {{domxref("HTMLButtonElement.formAction")}}
- {{domxref("HTMLButtonElement.formEnctype")}}
- {{domxref("HTMLButtonElement.formMethod")}}
- {{domxref("HTMLButtonElement.formTarget")}}
- {{HTMLElement("form")}}
- {{domxref("HTMLFormElement.noValidate")}}
- {{domxref("HTMLInputElement.formNoValidate")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)