---
title: "ElementInternals: ariaValueNow property"
short-title: ariaValueNow
slug: Web/API/ElementInternals/ariaValueNow
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaValueNow
---

{{APIRef("Web Components")}}

خاصیت `ariaValueNow` از رابط {{domxref("ElementInternals")}} منعکس‌کننده‌ی مقدار صفت [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) است که مقدار فعلی یک ویجت محدوده (range widget) را تعریف می‌کند.

> [!NOTE]
> تنظیم صفات aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض (default semantics) را برای یک عنصر سفارشی (custom element) فراهم می‌کند. این مقادیر ممکن است توسط صفات تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن صفات توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده‌ی مدل شیء دسترسی‌پذیری (Accessibility Object Model explainer)](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string) که شامل یک عدد است.

## مثال‌ها

در این مثال مقدار `ariaValueNow` به `"1"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaValueNow = "1";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}