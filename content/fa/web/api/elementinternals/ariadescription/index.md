---
title: "ElementInternals: ariaDescription property"
short-title: ariaDescription
slug: Web/API/ElementInternals/ariaDescription
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaDescription
---

{{APIRef("Web Components")}}

ویژگی **`ariaDescription`** در رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description) را بازتاب می‌دهد؛ ویژگی‌ای که یک رشته را تعریف می‌کند که عنصر فعلی را توصیف یا توضیح می‌دهد.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

در این مثال، مقدار `ariaDescription` روی «A description of this widget» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaDescription = "A description of this widget";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}