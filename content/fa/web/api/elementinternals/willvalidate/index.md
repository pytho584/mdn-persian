---
title: "ElementInternals: willValidate property"
short-title: willValidate
slug: Web/API/ElementInternals/willValidate
page-type: web-api-instance-property
browser-compat: api.ElementInternals.willValidate
---

{{APIRef("Web Components")}}

ویژگی فقط-خواندنی **`willValidate`** از رابط {{domxref("ElementInternals")}}، مقدار `true` را برمی‌گرداند اگر عنصر، یک عنصر قابل ارسال (submittable) باشد که کاندیدای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) است.

عناصری که از کاندیدا بودن برای اعتبارسنجی محدودیت‌ها منع شده‌اند شامل آنهایی هستند که ویژگی‌های `disabled`، `hidden` یا `readonly` را دارند، عناصر ورودی از نوع `type=button` یا `type=reset`، یا هر عنصری که یک عنصر {{htmlelement("datalist")}} باشد یا دارای یک عنصر جد `<datalist>` باشد.

## مقدار

اگر عنصر کاندیدای اعتبارسنجی محدودیت‌ها باشد `true`، در غیر این صورت `false`.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - اگر عنصر ویژگی `formAssociated` خود را برابر `true` تنظیم نکرده باشد، پرتاب می‌شود.

## مثال‌ها

مثال زیر یک مؤلفه چک‌باکس سفارشی را نشان می‌دهد که در آن `formAssociated` برابر `true` تنظیم شده است؛ مقدار `willValidate` در کنسول ثبت می‌شود.

```js
class CustomCheckbox extends HTMLElement {
  static formAssociated = true;

  constructor() {
    super();
    this.internals_ = this.attachInternals();
  }

  // …
}

window.customElements.define("custom-checkbox", CustomCheckbox);

let element = document.getElementById("custom-checkbox");
console.log(element.internals_.willValidate); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}