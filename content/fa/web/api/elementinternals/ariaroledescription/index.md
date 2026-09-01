```
---
title: "ElementInternals: ariaRoleDescription property"
short-title: ariaRoleDescription
slug: Web/API/ElementInternals/ariaRoleDescription
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaRoleDescription
---

{{APIRef("Web Components")}}

ویژگی **`ariaRoleDescription`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) را منعکس می‌کند. این ویژگی یک توضیح خوانا برای انسان و بومی‌سازی‌شده توسط نویسنده برای نقش یک عنصر تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria بر روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم اضافه کردن آن‌ها به طور کلی، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترسی‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

در این مثال مقدار `ariaRoleDescription` به "My custom widget" تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRoleDescription = "My custom widget";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش application](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
```