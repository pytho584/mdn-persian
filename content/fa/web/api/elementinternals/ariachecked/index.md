---
title: "ElementInternals: ariaChecked property"
short-title: ariaChecked
slug: Web/API/ElementInternals/ariaChecked
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaChecked
---

{{APIRef("Web Components")}}

ویژگی **`ariaChecked`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) است که وضعیت «تیک‌خورده» فعلی چک‌باکس‌ها، دکمه‌های رادیویی و سایر ویجت‌هایی که حالت تیک‌خورده دارند را نشان می‌دهد.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. ممکن است این مقادیر توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : عنصر تیک خورده است.
- `"mixed"`
  - : حالت ترکیبی را برای یک چک‌باکس یا منوی چک‌باکس (menuitemcheckbox) سه‌حالته نشان می‌دهد.
- `"false"`
  - : عنصر از تیک‌خوردن پشتیبانی می‌کند اما در حال حاضر تیک نخورده است.
- `"undefined"`
  - : عنصر از تیک‌خوردن پشتیبانی نمی‌کند.

## مثال‌ها

در این مثال مقدار `ariaChecked` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaChecked = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش checkbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)