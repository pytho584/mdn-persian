---
title: "HTMLSelectElement: validity property"
---

{{APIRef("HTML DOM")}}

خاصیت فقط خواندنی **`validity`** (به معنی اعتبار) از رابط {{domxref("HTMLSelectElement")}} یک شیء {{domxref("ValidityState")}} بازمی‌گرداند که وضعیت‌های اعتبار این عنصر را نشان می‌دهد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

## مثال

مثال زیر وضعیت اعتبار یک عنصر select را دریافت می‌کند و در صورت معتبر نبودن آن را پردازش می‌کند:

```js
const select = document.getElementById("mySelect");
const validityState = select.validity;
if (!validityState.valid) {
  // Test each validity state
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSelectElement.checkValidity()")}}
- {{HTMLElement("select")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)