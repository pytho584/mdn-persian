---
title: "ElementInternals: ariaPosInSet property"
---

---
title: "ElementInternals: ariaPosInSet property"
short-title: ariaPosInSet
slug: Web/API/ElementInternals/ariaPosInSet
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaPosInSet
---

{{APIRef("Web Components")}}

ویژگی **`ariaPosInSet`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) را منعکس می‌کند؛ ویژگی‌ای که شماره یا جایگاه یک عنصر را در مجموعهٔ فعلی از listitems یا treeitems تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای شامل یک عدد صحیح.

## نمونه‌ها

در این مثال، مقدار `ariaPosInSet` روی «2» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaPosInSet = "2";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}