---
title: "HTMLButtonElement: validity property"
short-title: validity
slug: Web/API/HTMLButtonElement/validity
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.validity
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validity`** در رابط {{domxref("HTMLButtonElement")}} یک شیء {{domxref("ValidityState")}} برمی‌گرداند که وضعیت‌های اعتبارسنجی این عنصر را نشان می‌دهد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال‌ها

مثال زیر نشان می‌دهد که یک `<button>` وقتی یک {{domxref("ValidityState/customError", "customError")}} تنظیم شده باشد در وضعیت نامعتبر قرار می‌گیرد؛ در این وضعیت، ویژگی `validity` در `validityState` برابر با `false` است، در حالی که {{domxref("HTMLButtonElement/checkValidity", "checkValidity()")}} اگر {{domxref("HTMLButtonElement/type", "type")}} دکمه `"submit"` نباشد `true` برمی‌گرداند، زیرا چنین دکمه‌هایی کاندیدای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

```js
const button = document.getElementById("myButton");
button.setCustomValidity("This button is invalid.");
const validityState = button.validity;
console.log(validityState.valid); // false
console.log(validityState.customError); // true
console.log(button.checkValidity()); // false if the button is of the "submit" type, true otherwise
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLButtonElement.checkValidity()")}}
- {{HTMLElement("button")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)