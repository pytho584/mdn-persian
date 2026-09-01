---
title: "ElementInternals: ariaRowSpan property"
short-title: ariaRowSpan
slug: Web/API/ElementInternals/ariaRowSpan
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaRowSpan
---

{{APIRef("Web Components")}}

ویژگی **`ariaRowSpan`** از رابط {{domxref("ElementInternals")}} مقدار [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan) را منعکس می‌کند؛ این ویژگی تعیین می‌کند که یک سلول یا gridcell در یک جدول، grid یا treegrid چند ردیف را پوشش می‌دهد.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی (custom element) فراهم می‌کند. ممکن است این مقادیر توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما این کار تضمین می‌کند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیحات مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای (string) شامل یک عدد صحیح.

## مثال‌ها

در این مثال، مقدار `ariaRowSpan` روی "2" تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRowSpan = "2";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [نقش table در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)