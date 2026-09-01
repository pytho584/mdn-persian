---
title: "ElementInternals: ariaReadOnly property"
short-title: ariaReadOnly
slug: Web/API/ElementInternals/ariaReadOnly
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaReadOnly
---

{{APIRef("Web Components")}}

ویژگی **`ariaReadOnly`** در رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly) است که نشان می‌دهد عنصر قابل ویرایش نیست، اما در سایر جنبه‌ها قابل استفاده است.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف یا عدم افزودن آن ویژگی‌ها توسط نویسنده، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : کاربر نمی‌تواند مقدار عنصر را تغییر دهد.
- `"false"`
  - : کاربر می‌تواند مقدار عنصر را تنظیم کند.

## مثال‌ها

در این مثال، مقدار `ariaReadOnly` روی `"true"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaReadonly = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش ARIA: textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)