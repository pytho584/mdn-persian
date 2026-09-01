---
title: "ElementInternals: ariaValueMax property"
short-title: ariaValueMax
slug: Web/API/ElementInternals/ariaValueMax
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaValueMax
---

{{APIRef("Web Components")}}

ویژگی **`ariaValueMax`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) است که حداکثر مقدار مجاز برای یک ویجت محدوده (range widget) را تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` به شما امکان می‌دهد که معناشناسی پیش‌فرض را برای یک عنصر سفارشی تعریف کنید. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آنها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل دسترسی‌پذیری اشیا (Accessibility Object Model explainer)](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته که شامل یک عدد است.

## مثال‌ها

در این مثال مقدار `ariaValueMax` روی "20" تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaValueMax = "20";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}