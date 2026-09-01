---
title: "ElementInternals: ariaMultiLine property"
short-title: ariaMultiLine
slug: Web/API/ElementInternals/ariaMultiLine
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaMultiLine
---

{{APIRef("Web Components")}}

ویژگی **`ariaMultiLine`** در رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار صفت [`aria-multiline`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiline) است که مشخص می‌کند یک جعبهٔ متن چند خط ورودی می‌پذیرد یا فقط یک خط.

> [!NOTE]
> تنظیم صفت‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط صفت‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن صفت‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : این یک جعبهٔ متن چندخطی است.
- `"false"`
  - : این یک جعبهٔ متن تک‌خطی است.

## مثال‌ها

در این مثال مقدار `ariaMultiLine` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaMultiLine = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [ARIA: نقش textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)