---
title: "ElementInternals: ariaSetSize property"
short-title: ariaSetSize
slug: Web/API/ElementInternals/ariaSetSize
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaSetSize
---

{{APIRef("Web Components")}}

خاصیت **`ariaSetSize`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) است که تعداد موارد موجود در مجموعه جاری از موارد لیست یا درخت را تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل دسترسی‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته حاوی یک عدد صحیح.

## مثال‌ها

در این مثال مقدار `ariaSetSize` به "4" تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaSetSize = "4";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نقش tab در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)