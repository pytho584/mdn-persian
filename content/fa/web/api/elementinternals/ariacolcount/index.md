---
title: "ElementInternals: ariaColCount property"
---

---
title: "ElementInternals: ariaColCount property"
short-title: ariaColCount
slug: Web/API/ElementInternals/ariaColCount
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaColCount
---

{{APIRef("Web Components")}}

ویژگی **`ariaColCount`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) است که تعداد ستون‌ها را در یک جدول، شبکه یا درخت‌شبکه تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که معناشناسی پیش‌فرض در صورت حذف یا نبود آن ویژگی‌ها حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

در این مثال، ویژگی [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) به «"3"» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaColCount = "3";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)