---
title: "HTMLInputElement: validity property"
short-title: validity
slug: Web/API/HTMLInputElement/validity
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.validity
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validity`** از رابط {{domxref("HTMLInputElement")}} یک شیء {{domxref("ValidityState")}} برمی‌گرداند که وضعیت‌های اعتبار (validity states) این عنصر را نشان می‌دهد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال‌ها

مثال زیر وضعیت اعتبار یک عنصر ورودی را دریافت می‌کند و اگر معتبر نباشد آن را پردازش می‌کند:

```js
const input = document.getElementById("myInput");
const validityState = input.validity;
if (!validityState.valid) {
  // Test each validity state
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.checkValidity()")}}
- {{HTMLElement("input")}}
- {{HTMLElement("form")}}
- [آموزش: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)