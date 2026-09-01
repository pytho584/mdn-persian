---
title: "ElementInternals: validationMessage property"
short-title: validationMessage
slug: Web/API/ElementInternals/validationMessage
page-type: web-api-instance-property
browser-compat: api.ElementInternals.validationMessage
---

{{APIRef("Web Components")}}

خاصیت فقطخواندنی **`validationMessage`** از رابط {{domxref("ElementInternals")}} پیام اعتبارسنجی عنصر را برمیگرداند.

## مقدار

رشتهای که شامل پیام اعتبارسنجی این عنصر است.

## مثالها

در مثال زیر، پیام اعتبارسنجی با {{domxref("ElementInternals.setValidity()")}} تنظیم شده و سپس با `validationMessage` برگردانده میشود.

```js
this.internals_.setValidity({ valueMissing: true }, "my message");
console.log(this.internals_.validationMessage); // "my message"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}