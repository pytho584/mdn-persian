---
title: "HTMLOutputElement: validity property"
short-title: validity
slug: Web/API/HTMLOutputElement/validity
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.validity
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validity`** در رابط {{domxref("HTMLOutputElement")}} یک شیء {{domxref("ValidityState")}} برمی‌گرداند که وضعیت‌های اعتبار این عنصر را نشان می‌دهد. اگرچه عناصر {{HTMLElement("output")}} هرگز نامزد [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند، اما اگر پیام اعتبار سفارشی تنظیم شده باشد، وضعیت اعتبار همچنان ممکن است نامعتبر باشد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال‌ها

مثال زیر نشان می‌دهد که یک `<output>` زمانی در وضعیت نامعتبر قرار می‌گیرد که یک {{domxref("ValidityState/customError", "customError")}} تنظیم شده باشد؛ در این حالت، {{domxref("HTMLOutputElement/checkValidity", "checkValidity()")}} مقدار `true` برمی‌گرداند، در حالی که ویژگی `validity` در `validityState` برابر `false` است.

```js
const output = document.getElementById("myOutput");
output.setCustomValidity("This object element is invalid.");
const validityState = output.validity;
console.log(validityState.valid); // false
console.log(validityState.customError); // true
console.log(output.checkValidity()); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLOutputElement.checkValidity()")}}
- {{HTMLElement("output")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)