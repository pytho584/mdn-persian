---
title: "HTMLFieldSetElement: setCustomValidity() method"
short-title: setCustomValidity()
slug: Web/API/HTMLFieldSetElement/setCustomValidity
page-type: web-api-instance-method
browser-compat: api.HTMLFieldSetElement.setCustomValidity
---

{{ APIRef("HTML DOM") }}

متد **`setCustomValidity()`** از رابط {{DOMxRef("HTMLFieldSetElement")}}، پیام اعتبارسنجی سفارشی را برای عنصر {{htmlelement("fieldset")}} تنظیم می‌کند. از رشتهٔ خالی استفاده کنید تا نشان دهید که عنصر خطای اعتبارسنجی سفارشی _ندارد_.

عنصر `<fieldset>` کاندیدای اعتبارسنجی محدودیت (constraint validation) نیست. متد {{DOMxRef("HTMLFieldSetElement.reportValidity()", "reportValidity()")}} باعث نمایش پیام خطای سفارشی به کاربر نمی‌شود، اما ویژگی {{DOMxRef("ValidityState.customError", "customError")}} از شیء {{DOMxRef("ValidityState")}} عنصر را به `true` و ویژگی {{DOMxRef("ValidityState.valid", "valid")}} را به `false` تنظیم می‌کند.

## نحو

```js-nolint
setCustomValidity(string)
```

### پارامترها

- `string`
  - : رشته‌ای که شامل پیام خطا است. رشتهٔ خالی هر گونه خطای اعتبارسنجی سفارشی را حذف می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
const errorFieldSet = document.getElementById("checkErrors");
const errors = issuesToReport();
if (errors) {
  errorFieldSet.setCustomValidity("There is an error");
} else {
  errorFieldSet.setCustomValidity("");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLelement("fieldset")}}
- {{domxref("HTMLFieldSetElement")}}
- {{domxref("HTMLFieldSetElement.validity")}}
- {{domxref("HTMLFieldSetElement.checkValidity()")}}
- {{domxref("HTMLFieldSetElement.reportValidity()")}}
- [اعتبارسنجی فرم](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}