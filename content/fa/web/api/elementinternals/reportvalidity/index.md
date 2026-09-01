---
title: "ElementInternals: reportValidity() method"
short-title: reportValidity()
slug: Web/API/ElementInternals/reportValidity
page-type: web-api-instance-method
browser-compat: api.ElementInternals.reportValidity
---

{{APIRef("Web Components")}}

متد **`reportValidity()`** از رابط {{domxref("ElementInternals")}} بررسی می‌کند که آیا عنصر با قوانین [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال‌شده بر آن مطابقت دارد یا خیر.

اگر `reportValidity` مقدار `false` برگرداند، یک رویداد [invalid](/en-US/docs/Web/API/HTMLInputElement/invalid_event) قابل‌لغو روی عنصر فعال می‌شود.

این متد رفتاری مشابه {{domxref("ElementInternals.checkValidity()")}} دارد، اما علاوه بر آن مقدار {{domxref("ElementInternals.validationMessage")}} را برای نمایش به عامل کاربر ارسال می‌کند.

## نحو (Syntax)

```js-nolint
reportValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولی؛ اگر عنصر با تمام محدودیت‌های اعتبارسنجی مطابقت داشته باشد، `true` است.

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر ویژگی `formAssociated` عنصر روی `true` تنظیم نشده باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر از {{domxref("ElementInternals.setValidity()")}} برای نشان دادن اینکه عنصر قوانین اعتبارسنجی را برآورده نمی‌کند استفاده شده است. فراخوانی `reportValidity()` مقدار `false` برمی‌گرداند و مقدار «my message» برای نمایش به عامل کاربر ارسال می‌شود.

پس از فراخوانی دوباره `setValidity`، این بار با نشان دادن اینکه همه قوانین برآورده شده‌اند، `reportValidity()` مقدار `true` برمی‌گرداند.

```js
let element = document.getElementById("join-checkbox");
element.internals_.setValidity({ valueMissing: true }, "my message");
console.log(element.internals_.reportValidity()); // false
element.internals_.setValidity({});
console.log(element.internals_.reportValidity()); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}