---
title: "ElementInternals: ariaCurrent property"
short-title: ariaCurrent
slug: Web/API/ElementInternals/ariaCurrent
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaCurrent
---

{{APIRef("Web Components")}}

ویژگی **`ariaCurrent`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-current`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-current) را منعکس می‌کند. این ویژگی نشان‌دهنده عنصری است که آیتم جاری را در یک ظرف یا مجموعه‌ای از عناصر مرتبط مشخص می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` به شما امکان می‌دهد معناشناسی پیش‌فرض را برای یک عنصر سفارشی تعریف کنید. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترسی‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"page"`
  - : نشان‌دهنده صفحه جاری در یک مجموعه از صفحات است.
- `"step"`
  - : نشان‌دهنده گام جاری در یک فرآیند است.
- `"location"`
  - : نشان‌دهنده مکان جاری، مثلاً صفحه جاری در یک سلسله‌مراتب خرده‌نان (breadcrumbs) است.
- `"date"`
  - : نشان‌دهنده تاریخ جاری در یک مجموعه از تاریخ‌ها است.
- `"time"`
  - : نشان‌دهنده زمان جاری در یک مجموعه از زمان‌ها است.
- `"true"`
  - : نشان‌دهنده آیتم جاری در یک مجموعه است.
- `"false"`
  - : نشان‌دهنده آیتم جاری در یک مجموعه نیست.

## مثال‌ها

در این مثال مقدار `ariaCurrent` روی `"page"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaCurrent = "page";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از ویژگی aria-current](https://tink.uk/using-the-aria-current-attribute/)