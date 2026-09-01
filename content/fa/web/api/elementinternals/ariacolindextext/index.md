---
title: ElementInternals.ariaColIndexText
slug: Web/API/ElementInternals/ariaColIndexText
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaColIndexText
---

{{APIRef("Web Components")}}

ویژگی **`ariaColIndexText`** در رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-colindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext) است که یک جایگزین متنی قابل‌خواندن برای انسان برای `aria-colindex` تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های ARIA روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر می‌توانند توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اطمینان می‌دهند که در صورت حذف یا عدم افزودن آن ویژگی‌ها توسط نویسنده، معناشناسی پیش‌فرض حفظ می‌شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته.

## مثال

در این مثال، مقدار `ariaColIndexText` روی «Column name» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaColIndexText = "Column name";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)