---
title: "ElementInternals: ariaLabel property"
short-title: ariaLabel
slug: Web/API/ElementInternals/ariaLabel
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaLabel
---

{{APIRef("Web Components")}}

خاصیت **`ariaLabel`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) است که یک رشته مقداری را تعریف می‌کند که عنصر جاری را برچسب‌گذاری می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria بر روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترسی‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

در این مثال مقدار `ariaLabel` به `"close"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaLabel = "close";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}