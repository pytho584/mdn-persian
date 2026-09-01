---
title: "ElementInternals: ariaExpanded property"
short-title: ariaExpanded
slug: Web/API/ElementInternals/ariaExpanded
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaExpanded
---

{{APIRef("Web Components")}}

ویژگی **`ariaExpanded`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) را منعکس می‌کند. این ویژگی نشان می‌دهد که آیا عنصر گروه‌بندی که متعلق به این عنصر است یا توسط آن کنترل می‌شود، باز (گسترده) است یا بسته (جمع‌شده).

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : عنصر گروه‌بندی که این عنصر مالک یا کنترل‌کنندهٔ آن است، باز (گسترده) است.
- `"false"`
  - : عنصر گروه‌بندی که این عنصر مالک یا کنترل‌کنندهٔ آن است، بسته (جمع‌شده) است.
- `"undefined"`
  - : عنصر مالک یا کنترل‌کنندهٔ یک عنصر گروه‌بندی قابل‌بازشدن نیست.

## مثال‌ها

در این مثال مقدار `ariaExpanded` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaInvalid = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}