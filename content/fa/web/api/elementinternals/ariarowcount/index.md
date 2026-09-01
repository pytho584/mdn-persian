---
title: "ElementInternals: ariaRowCount property"
short-title: ariaRowCount
slug: Web/API/ElementInternals/ariaRowCount
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaRowCount
---

{{APIRef("Web Components")}}

ویژگی **`ariaRowCount`** از رابط {{domxref("ElementInternals")}}، مقدار ویژگی [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) را منعکس می‌کند که تعداد کل ردیف‌ها را در یک جدول، grid یا treegrid تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این معناشناسی‌ها ممکن است توسط ویژگی‌های تعریف‌شدهٔ نویسنده بازنویسی شوند، اما در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ می‌شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای شامل یک عدد صحیح.

## مثال‌ها

در این مثال، مقدار `ariaRowCount` روی «100» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRowCount = "100";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)