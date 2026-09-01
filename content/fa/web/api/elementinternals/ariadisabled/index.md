---
title: "ElementInternals: ariaDisabled property"
short-title: ariaDisabled
slug: Web/API/ElementInternals/ariaDisabled
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaDisabled
---

{{APIRef("Web Components")}}

ویژگی **`ariaDisabled`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) است که نشان می‌دهد عنصر قابل درک است اما غیرفعال شده و بنابراین قابل ویرایش یا تعامل نیست.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اطمینان حاصل می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : عنصر و همهٔ عناصر فرزند قابل فوکوس غیرفعال هستند، اما قابل درک‌اند و کاربر نمی‌تواند مقادیر آن‌ها را تغییر دهد.
- `"false"`
  - : عنصر فعال است.

## مثال‌ها

در این مثال مقدار `ariaDisabled` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaDisabled = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}