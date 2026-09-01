---
title: "ElementInternals: ariaColIndex property"
---

---
title: "ElementInternals: ariaColIndex property"
short-title: ariaColIndex
slug: Web/API/ElementInternals/ariaColIndex
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaColIndex
---

{{APIRef("Web Components")}}

**`ariaColIndex`** ویژگیای از رابط {{domxref("ElementInternals")}} است که مقدار ویژگی [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) را منعکس میکند. این ویژگی، ایندکس یا موقعیت ستون یک عنصر را نسبت به تعداد کل ستونها در یک جدول، grid یا treegrid تعریف میکند.

> [!NOTE]
> تنظیم ویژگیهای aria روی `ElementInternals` امکان تعریف معناشناسی پیشفرض را روی یک عنصر سفارشی (custom element) فراهم میکند. این ویژگیها ممکن است توسط ویژگیهای تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [Accessibility Object Model explainer](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string) که شامل یک عدد صحیح است.

## مثال‌ها

در این مثال، مقدار `ariaColIndex` روی «"2"» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaColIndex = "2";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: table role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)