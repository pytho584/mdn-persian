```markdown
---
title: "ElementInternals: validity property"
short-title: validity
slug: Web/API/ElementInternals/validity
page-type: web-api-instance-property
browser-compat: api.ElementInternals.validity
---

{{APIRef("Web Components")}}

خاصیت فقط خواندنی **`validity`** در رابط {{domxref("ElementInternals")}} یک شیء {{domxref("ValidityState")}} را برمی‌گرداند که وضعیت‌های اعتبار مختلفی را که عنصر می‌تواند داشته باشد، در رابطه با اعتبارسنجی محدودیت‌ها (constraint validation) نشان می‌دهد.

## مقدار

یک شیء {{domxref("ValidityState")}}.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر عنصر خاصیت `formAssociated` خود را روی `true` تنظیم نکرده باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک مؤلفه‌ی چک‌باکس سفارشی با `formAssociated` تنظیم شده روی `true` نشان داده شده است. مقدار `validity.valid` در کنسول ثبت می‌شود.

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
console.log(element.internals_.validity.valid);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```