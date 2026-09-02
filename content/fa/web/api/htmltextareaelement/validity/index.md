---
title: "HTMLTextAreaElement: validity property"
short-title: validity
slug: Web/API/HTMLTextAreaElement/validity
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.validity
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validity`** در رابط {{domxref("HTMLTextAreaElement")}} یک شیء {{domxref("ValidityState")}} برمی‌گرداند که وضعیت‌های اعتبارسنجی این عنصر را نشان می‌دهد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال‌ها

مثال زیر وضعیت اعتبارسنجی یک عنصر ناحیه متنی را دریافت می‌کند و اگر معتبر نبود آن را پردازش می‌کند:

```js
const textArea = document.getElementById("myTextArea");
const validityState = textArea.validity;
if (!validityState.valid) {
  // Test each validity state
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTextAreaElement.checkValidity()")}}
- {{HTMLElement("textarea")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)