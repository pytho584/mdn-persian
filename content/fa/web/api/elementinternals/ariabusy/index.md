---
title: "ElementInternals: ariaBusy property"
short-title: ariaBusy
slug: Web/API/ElementInternals/ariaBusy
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaBusy
---

{{APIRef("Web Components")}}

ویژگی **`ariaBusy`** از رابط {{domxref("ElementInternals")}}، مقدار [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) را بازتاب می‌دهد؛ این ویژگی مشخص می‌کند که آیا یک عنصر در حال تغییر است، زیرا فناوری‌های کمکی ممکن است بخواهند تا تکمیل تغییرات صبر کنند و سپس آن‌ها را در اختیار کاربر قرار دهند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این معناشناسی‌های پیش‌فرض ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً اضافه نکند، معناشناسی پیش‌فرض حفظ می‌شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر در حال به‌روزرسانی است.
- `"false"`
  - : هیچ به‌روزرسانی مورد انتظاری برای عنصر وجود ندارد.

## مثال‌ها

در این مثال، مقدار `ariaBusy` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaBusy = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
