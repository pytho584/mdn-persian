---
title: "ElementInternals: ariaValueMin property"
---

---
title: "ElementInternals: ariaValueMin property"
short-title: ariaValueMin
slug: Web/API/ElementInternals/ariaValueMin
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaValueMin
---

{{APIRef("Web Components")}}

ویژگی **`ariaValueMin`** در رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) است که کمترین مقدار مجاز را برای یک ابزارک محدوده (range widget) تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` این امکان را فراهم می‌کند که معناشناسی پیش‌فرض (default semantics) برای یک عنصر سفارشی (custom element) تعریف شود. ممکن است این ویژگی‌ها توسط ویژگی‌هایی که نویسنده تعریف می‌کند بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکرده باشد، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [مستند توضیحی مدل شیء دسترس‌پذیری (Accessibility Object Model)](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string) که شامل یک عدد است.

## مثال‌ها

در این مثال، مقدار `ariaValueMin` روی «10» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaValueMin = "10";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}