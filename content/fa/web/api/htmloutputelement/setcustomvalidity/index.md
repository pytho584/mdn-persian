---
title: "HTMLOutputElement: setCustomValidity() method"
short-title: setCustomValidity()
slug: Web/API/HTMLOutputElement/setCustomValidity
page-type: web-api-instance-method
browser-compat: api.HTMLOutputElement.setCustomValidity
---

{{ APIRef("HTML DOM") }}

متد **`setCustomValidity()`** در رابط {{DOMxRef("HTMLOutputElement")}} پیام اعتبارسنجی سفارشی را برای عنصر {{htmlelement("output")}} تنظیم می‌کند. برای نشان دادن اینکه عنصر خطای اعتبارسنجی سفارشی _ندارد_، از رشته خالی استفاده کنید.

عنصر `<output>` کاندیدای اعتبارسنجی محدودیت‌ها (constraint validation) نیست. متد {{DOMxRef("HTMLOutputElement.reportValidity()", "reportValidity()")}} باعث نمایش پیام خطای سفارشی به کاربر نمی‌شود، اما ویژگی {{DOMxRef("ValidityState.customError", "customError")}} را در شیء {{DOMxRef("ValidityState")}} عنصر روی `true` و ویژگی {{DOMxRef("ValidityState.valid", "valid")}} را روی `false` تنظیم می‌کند.

## نحو

```js-nolint
setCustomValidity(string)
```

### پارامترها

- `string`
  - رشته‌ای شامل پیام خطا. رشته خالی هر خطای اعتبارسنجی سفارشی را حذف می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

در این مثال، اگر {{domxref("HTMLOutputElement.value", "value")}} عنصر `<output>` یک عدد غیر از صفر نباشد، یک پیام خطای سفارشی تنظیم می‌کنیم. اگر عدد باشد، خطای سفارشی را روی رشته خالی تنظیم می‌کنیم:

```js
const cart = document.getElementById("cart-form");
const total = cart.elements("total");
if (parseFloat(total.value)) {
  errorOutput.setCustomValidity("");
} else {
  errorOutput.setCustomValidity("یک خطا رخ داده است");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLelement("output")}}
- {{domxref("HTMLOutputElement")}}
- {{domxref("HTMLOutputElement.validity")}}
- {{domxref("HTMLOutputElement.checkValidity()")}}
- {{domxref("HTMLOutputElement.reportValidity()")}}
- [اعتبارسنجی فرم](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}