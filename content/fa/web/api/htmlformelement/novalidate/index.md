---
title: "HTMLFormElement: noValidate property"
short-title: noValidate
slug: Web/API/HTMLFormElement/noValidate
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.noValidate
---

{{APIRef("HTML DOM")}}

ویژگی **`noValidate`** از رابط {{domxref("HTMLFormElement")}} یک مقدار بولی است که نشان می‌دهد آیا {{htmlelement("form")}} هنگام ارسال، [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) را دور می‌زند یا خیر. این ویژگی منعکس‌کنندهٔ ویژگی [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) عنصر `<form>` است؛ اگر ویژگی وجود داشته باشد، مقدار آن `true` است.

اگر این ویژگی تنظیم نشده باشد یا مقدار آن `false` باشد، فرم اعتبارسنجی می‌شود. این رفتار می‌تواند با تنظیم ویژگی {{domxref("HTMLInputElement.formNoValidate")}} یا {{domxref("HTMLButtonElement.formNoValidate")}} به `true`، چه از طریق JavaScript و چه از طریق ویژگی HTML `formnovalidate`، برای کنترل‌کنندهٔ ارسال فرم، لغو شود.

این ویژگی قابل دریافت و تنظیم است.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const element = document.getElementById("myForm");
console.log(element.noValidate);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFormElement.reportValidity()")}}
- {{domxref("HTMLFormElement.checkValidity()")}}
- {{domxref("HTMLFormElement.action")}}
- {{domxref("HTMLFormElement.enctype")}}
- {{domxref("HTMLFormElement.method")}}
- {{domxref("HTMLFormElement.target")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)