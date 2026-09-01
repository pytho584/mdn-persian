---
title: "ElementInternals: ariaMultiSelectable property"
short-title: ariaMultiSelectable
slug: Web/API/ElementInternals/ariaMultiSelectable
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaMultiSelectable
---

{{APIRef("Web Components")}}

ویژگی **`ariaMultiSelectable`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-multiselectable`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable) را منعکس می‌کند که نشان می‌دهد آیا کاربر می‌تواند بیش از یک مورد را از میان فرزندان قابل انتخاب فعلی انتخاب کند یا خیر.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که معناشناسی پیش‌فرض در صورت حذف آن ویژگی‌ها توسط نویسنده، یا عدم افزودن آن‌ها، حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : بیش از یک مورد می‌تواند در یک زمان انتخاب شود.
- `"false"`
  - : فقط یک مورد می‌تواند انتخاب شود.

## مثال‌ها

در این مثال، مقدار `ariaMultiSelectable` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaMultiSelectable = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش listbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)