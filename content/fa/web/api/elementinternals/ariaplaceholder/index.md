---
title: "ElementInternals: ariaPlaceholder property"
short-title: ariaPlaceholder
slug: Web/API/ElementInternals/ariaPlaceholder
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaPlaceholder
---

{{APIRef("Web Components")}}

ویژگی **`ariaPlaceholder`** در رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-placeholder`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-placeholder) را بازتاب می‌دهد. این ویژگی یک راهنمای کوتاه تعریف می‌کند که برای کمک به کاربر در ورود داده، هنگامی که کنترل مقداری ندارد، در نظر گرفته شده است.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. ممکن است این ویژگی‌ها توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکرده باشد، معناشناسی پیش‌فرض حفظ می‌شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

در این مثال، مقدار `ariaPlaceholder` به «12345» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaPlaceholder = "12345";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش textbox در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)