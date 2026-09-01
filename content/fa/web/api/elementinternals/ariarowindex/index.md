---
title: "ElementInternals: ariaRowIndex property"
---

---
title: "ElementInternals: ariaRowIndex property"
short-title: ariaRowIndex
slug: Web/API/ElementInternals/ariaRowIndex
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaRowIndex
---

{{APIRef("Web Components")}}

ویژگی **`ariaRowIndex`** در رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) است؛ ویژگی‌ای که اندیس یا موقعیت ردیف یک عنصر را نسبت به تعداد کل ردیف‌ها در یک جدول (table)، گرید (grid) یا درخت‌گرید (treegrid) تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض (default semantics) را روی یک عنصر سفارشی (custom element) فراهم می‌کند. این معناشناسی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما در صورت حذف آن ویژگی‌ها توسط نویسنده یا اصلاً افزوده نشدن آن‌ها، حفظ معناشناسی پیش‌فرض را تضمین می‌کنند. برای اطلاعات بیشتر به [توضیح‌دهندهٔ مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string) که شامل یک عدد صحیح (integer) است.

## مثال‌ها

در این مثال، مقدار `ariaRowIndex` روی «1» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRowIndex = "1";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: table role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)