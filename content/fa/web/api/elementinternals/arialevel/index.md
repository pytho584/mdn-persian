---
title: "ElementInternals: ariaLevel property"
short-title: ariaLevel
slug: Web/API/ElementInternals/ariaLevel
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaLevel
---

{{APIRef("Web Components")}}

ویژگی **`ariaLevel`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level) است که سطح سلسله‌مراتبی یک عنصر را در یک ساختار تعریف می‌کند.

> [!NOTE]
> تنظیم صفات aria روی `ElementInternals` امکان تعریف معناشناسی (semantics) پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این صفات ممکن است توسط صفات تعریف‌شده توسط نویسنده بازنویسی شوند، اما اطمینان حاصل می‌شود که اگر نویسنده آن صفات را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطالع بیشتر به [توضیح‌دهنده مدل دسترسی‌پذیری (Accessibility Object Model explainer)](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته شامل یک عدد صحیح.

## نمونه‌ها

در این مثال، مقدار `ariaLevel` به `"1"` تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaLevel = "1";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همجنین ببینید

- [ARIA: heading role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role)