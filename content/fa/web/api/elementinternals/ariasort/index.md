---
title: "ElementInternals: ariaSort property"
short-title: ariaSort
slug: Web/API/ElementInternals/ariaSort
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaSort
---

{{APIRef("Web Components")}}

ویژگی **`ariaSort`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار صفت [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) است که نشان می‌دهد آیا آیتم‌های یک جدول یا گرید به ترتیب صعودی یا نزولی مرتب شده‌اند.

> [!NOTE]
> تنظیم صفت‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط صفت‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف یا عدم افزودن آن صفت‌ها توسط نویسنده، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهندهٔ مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"ascending"`
  - : آیتم‌ها بر اساس این ستون به ترتیب صعودی مرتب شده‌اند.
- `"descending"`
  - : آیتم‌ها بر اساس این ستون به ترتیب نزولی مرتب شده‌اند.
- `"none"`
  - : هیچ ترتیب‌سازی مشخصی برای ستون اعمال نشده است.
- `"other"`
  - : الگوریتم مرتب‌سازی دیگری غیر از صعودی یا نزولی اعمال شده است.

## مثال‌ها

در این مثال، مقدار `ariaSort` روی «ascending» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaSort = "ascending";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)