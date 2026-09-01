---
title: "HTMLFieldSetElement: validity property"
short-title: validity
slug: Web/API/HTMLFieldSetElement/validity
page-type: web-api-instance-property
browser-compat: api.HTMLFieldSetElement.validity
---

{{APIRef("HTML DOM")}}

خاصیت فقط‌خواندنی **`validity`** در رابط {{domxref("HTMLFieldSetElement")}} یک شیء {{domxref("ValidityState")}} برمی‌گرداند که وضعیت‌های اعتبار این عنصر را نشان می‌دهد. اگرچه عناصر {{HTMLElement("fieldset")}} هرگز کاندیدای [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند، اگر یک پیام اعتبار سفارشی تنظیم شده باشد، وضعیت اعتبار ممکن است همچنان نامعتبر باشد.

> [!NOTE]
> شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}} بر اساس اعتبار کنترل‌های فرمِ فرزندِ عنصر `<fieldset>` روی آن اعمال می‌شوند، نه بر اساس خودِ fieldset.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال‌ها

مثال زیر نشان می‌دهد که یک `<fieldset>` زمانی که یک {{domxref("ValidityState/customError", "customError")}} تنظیم شده باشد در وضعیت نامعتبر قرار می‌گیرد؛ در این حالت، {{domxref("HTMLFieldSetElement/checkValidity", "checkValidity()")}} مقدار `true` برمی‌گرداند در حالی که ویژگی `validity` در `validityState` برابر `false` است.

```js
const fieldSet = document.getElementById("myFieldSet");
fieldSet.setCustomValidity("This fieldset is invalid.");
const validityState = fieldSet.validity;
console.log(validityState.valid); // false
console.log(validityState.customError); // true
console.log(fieldSet.checkValidity()); // true
```

> [!NOTE]
> شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}} بر اساس اعتبار کنترل‌های فرمِ فرزندِ عنصر `<fieldset>` روی آن اعمال می‌شوند، نه بر اساس خودِ fieldset.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFieldSetElement.checkValidity()")}}
- {{HTMLElement("fieldset")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)