---
title: "ElementInternals: checkValidity() method"
short-title: checkValidity()
slug: Web/API/ElementInternals/checkValidity
page-type: web-api-instance-method
browser-compat: api.ElementInternals.checkValidity
---

{{APIRef("Web Components")}}

متد **`checkValidity()`** از رابط {{domxref("ElementInternals")}} بررسی می‌کند که آیا عنصر، تمام قوانین [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال‌شده بر روی خود را برآورده می‌کند یا خیر.

اگر `checkValidity` مقدار `false` برگرداند، یک [رویداد invalid] قابل‌لغو (/en-US/docs/Web/API/HTMLInputElement/invalid_event) روی عنصر صادر می‌شود.

## نحو (Syntax)

```js-nolint
checkValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولی؛ اگر عنصر تمام محدودیت‌های اعتبارسنجی را برآورده کند `true` است.

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر ویژگی `formAssociated` عنصر روی `true` تنظیم نشده باشد، این خطا پرتاب می‌شود.

## مثال‌ها

در مثال زیر، از {{domxref("ElementInternals.setValidity()")}} برای نشان‌دادن این استفاده شده است که عنصر قوانین اعتبارسنجی را برآورده نمی‌کند. فراخوانی `checkValidity()` مقدار `false` برمی‌گرداند. پس از فراخوانی دوباره `setValidity`، این بار با نشان‌دادن اینکه همه قوانین برآورده شده‌اند، `checkValidity()` مقدار `true` برمی‌گرداند.

```js
let element = document.getElementById("join-checkbox");
element.internals_.setValidity({ valueMissing: true }, "my message");
console.log(element.internals_.checkValidity()); // false
element.internals_.setValidity({});
console.log(element.internals_.checkValidity()); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}
```