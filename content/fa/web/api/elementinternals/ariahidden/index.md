---
title: "ElementInternals: ariaHidden property"
short-title: ariaHidden
slug: Web/API/ElementInternals/ariaHidden
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaHidden
---

{{APIRef("Web Components")}}

ویژگی **`ariaHidden`** در رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار صفت [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) است که مشخص می‌کند آیا عنصر در معرض یک API دسترسی‌پذیری قرار می‌گیرد یا خیر.

> [!NOTE]
> تنظیم صفات aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این موارد ممکن است توسط صفات تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن صفات را حذف کند یا اصلاً اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهندهٔ مدل شیء دسترسی‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر از API دسترسی‌پذیری پنهان است.
- `"false"`
  - : عنصر به API دسترسی‌پذیری نمایش داده می‌شود، گویی که رندر شده است.
- `"undefined"`
  - : وضعیت پنهان بودن عنصر توسط عامل کاربر بر اساس اینکه آیا رندر شده است تعیین می‌شود.

## مثال‌ها

در این مثال، مقدار `ariaHidden` روی `"true"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaHidden = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}