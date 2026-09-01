---
title: ElementInternals.ariaRowIndexText
slug: Web/API/ElementInternals/ariaRowIndexText
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaRowIndexText
---

{{APIRef("Web Components")}}

ویژگی **`ariaRowIndexText`** از رابط {{domxref("ElementInternals")}}، مقدار ویژگی [`aria-rowindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext) را منعکس می‌کند؛ ویژگی‌ای که یک جایگزین متنیِ قابل‌خواندن برای انسان برای `aria-rowindex` تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. ممکن است این مقادیر توسط ویژگی‌های تعریف‌شدهٔ نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده، یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهندهٔ مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string).

## نمونه

در این مثال، مقدار `ariaRowIndexText` روی «Heading row» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRowIndexText = "Heading row";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش جدول ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)