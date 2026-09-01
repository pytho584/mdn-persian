---
title: "ElementInternals: ariaValueText property"
short-title: ariaValueText
slug: Web/API/ElementInternals/ariaValueText
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaValueText
---

{{APIRef("Web Components")}}

خاصیت **`ariaValueText`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) است که متن جایگزین قابل‌فهم برای انسان برای `aria-valuenow` در یک ویجت محدوده (range widget) تعریف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string).

## مثال‌ها

در این مثال، مقدار `ariaValueText` روی «Sunday» تنظیم می‌شود.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaValueText = "Sunday";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}