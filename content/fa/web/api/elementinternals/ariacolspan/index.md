---
title: "ElementInternals: ariaColSpan property"
short-title: ariaColSpan
slug: Web/API/ElementInternals/ariaColSpan
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaColSpan
---

{{APIRef("Web Components")}}

ویژگی **`ariaColSpan`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan) را بازتاب می‌دهد که تعداد ستون‌های پوشش‌داده‌شده توسط یک سلول یا سلول شبکه‌ای را در یک جدول، شبکه یا درخت‌شبکه تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، اطمینان از حفظ معناشناسی پیش‌فرض می‌دهند. برای اطلاعات بیشتر، [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) را ببینید.

## مقدار

رشته‌ای که شامل یک عدد صحیح است.

## مثال‌ها

در این مثال مقدار `ariaColspan` روی «2» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaColspan = "2";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)