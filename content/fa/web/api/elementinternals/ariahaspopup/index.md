---
title: "ElementInternals: ariaHasPopup property"
short-title: ariaHasPopup
slug: Web/API/ElementInternals/ariaHasPopup
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaHasPopup
---

{{APIRef("Web Components")}}

ویژگی **`ariaHasPopup`** در رابط {{domxref("ElementInternals")}}، مقدار ویژگی [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) را منعکس می‌کند که نشان‌دهنده وجود و نوع عنصر بازشوی تعاملی (مانند منو یا دیالوگ) است که می‌تواند توسط یک عنصر فعال شود.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معنای پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معنای پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"false"`
  - : عنصر هیچ عنصر بازشویی ندارد.
- `"true"`
  - : عنصر دارای یک عنصر بازشو از نوع منو است.
- `"menu"`
  - : عنصر دارای یک عنصر بازشو از نوع منو است.
- `"listbox"`
  - : عنصر دارای یک عنصر بازشو از نوع فهرست (listbox) است.
- `"tree"`
  - : عنصر دارای یک عنصر بازشو از نوع درخت (tree) است.
- `"grid"`
  - : عنصر دارای یک عنصر بازشو از نوع شبکه (grid) است.
- `"dialog"`
  - : عنصر دارای یک عنصر بازشو از نوع دیالوگ است.

## مثال‌ها

در این مثال، مقدار `ariaHasPopup` روی `"true"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaHasPopup = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}