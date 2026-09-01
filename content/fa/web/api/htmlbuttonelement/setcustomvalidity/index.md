---
title: "HTMLButtonElement: setCustomValidity() method"
short-title: setCustomValidity()
slug: Web/API/HTMLButtonElement/setCustomValidity
page-type: web-api-instance-method
browser-compat: api.HTMLButtonElement.setCustomValidity
---

{{ APIRef("HTML DOM") }}

متد **`setCustomValidity()`** از رابط {{DOMxRef("HTMLButtonElement")}} پیام اعتبارسنجی سفارشی را برای عنصر {{htmlelement("button")}} تنظیم می‌کند. برای نشان دادن اینکه عنصر خطای اعتبارسنجی سفارشی _ندارد_، از رشتهٔ خالی استفاده کنید.

## نحو

```js-nolint
setCustomValidity(string)
```

### پارامترها

- `string`
  - : رشته‌ای که پیام خطا را در بر می‌گیرد. رشتهٔ خالی هر خطای اعتبارسنجی سفارشی را حذف می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const errorButton = document.getElementById("checkErrors");
const errors = issuesToReport();
if (errors) {
  errorButton.setCustomValidity("There is an error");
} else {
  errorButton.setCustomValidity("");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLelement("button")}}
- {{domxref("HTMLButtonElement")}}
- {{domxref("HTMLButtonElement.validity")}}
- {{domxref("HTMLButtonElement.checkValidity()")}}
- {{domxref("HTMLButtonElement.reportValidity()")}}
- [اعتبارسنجی فرم](/en-US/docs/Web/HTML/Guides/Constraint_validation).
- [یادگیری: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}