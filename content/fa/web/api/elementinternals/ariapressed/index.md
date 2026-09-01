---
title: "ElementInternals: ariaPressed property"
short-title: ariaPressed
slug: Web/API/ElementInternals/ariaPressed
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaPressed
---

{{APIRef("Web Components")}}

ویژگی **`ariaPressed`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) را منعکس می‌کند که وضعیت «فشرده» فعلی دکمه‌های تغییر وضعیت (toggle buttons) را نشان می‌دهد.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اطمینان حاصل می‌شود که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ می‌شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر فشرده شده است.
- `"false"`
  - : عنصر قابلیت فشرده شدن را دارد اما در حال حاضر فشرده نیست.
- `"mixed"`
  - : یک مقدار حالت ترکیبی برای دکمه تغییر وضعیت سه‌حالته را نشان می‌دهد.
- `"undefined"`
  - : عنصر از فشرده شدن پشتیبانی نمی‌کند.

## مثال‌ها

در این مثال، مقدار `ariaPressed` روی "true" تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaPressed = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نقش دکمه ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)