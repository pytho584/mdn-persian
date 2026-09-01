---
title: "HTMLObjectElement: validity property"
short-title: validity
slug: Web/API/HTMLObjectElement/validity
page-type: web-api-instance-property
browser-compat: api.HTMLObjectElement.validity
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validity`** در رابط {{domxref("HTMLObjectElement")}} یک شیء {{domxref("ValidityState")}} برمی‌گرداند که وضعیت‌های اعتبار این عنصر را نشان می‌دهد. اگرچه عناصر {{HTMLElement("object")}} هرگز کاندیدای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند، اما اگر پیام اعتبار سفارشی تنظیم شده باشد، وضعیت اعتبار ممکن است همچنان نامعتبر باشد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال‌ها

مثال زیر نشان می‌دهد که وقتی یک {{domxref("ValidityState/customError", "customError")}} تنظیم شود، یک `<object>` در وضعیت نامعتبر قرار دارد؛ در این وضعیت، {{domxref("HTMLObjectElement/checkValidity", "checkValidity()")}} مقدار `true` را برمی‌گرداند، در حالی که ویژگی `validity` متعلق به `validityState` برابر با `false` است.

```js
const objectElem = document.getElementById("myObjectElm");
objectElem.setCustomValidity("This object element is invalid.");
const validityState = objectElem.validity;
console.log(validityState.valid); // false
console.log(validityState.customError); // true
console.log(objectElem.checkValidity()); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLObjectElement.checkValidity()")}}
- {{HTMLElement("object")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)