---
title: "ElementInternals: ariaRelevant property"
short-title: ariaRelevant
slug: Web/API/ElementInternals/ariaRelevant
page-type: web-api-instance-property
status:
  - non-standard
browser-compat: api.ElementInternals.ariaRelevant
---

{{APIRef("Web Components")}}{{Non-standard_header}}

ویژگی **`ariaRelevant`** در رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) را منعکس می‌کند؛ این ویژگی مشخص می‌کند که عامل کاربر با تغییر درخت دسترس‌پذیری درون یک منطقهٔ زنده (live region)، چه اعلان‌هایی را فعال کند. از این ویژگی برای توصیف این استفاده می‌شود که کدام تغییرات در یک منطقهٔ `aria-live` مرتبط هستند و باید اعلام شوند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض برای یک عنصر سفارشی را فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته شامل یک یا چند مورد از مقادیر زیر، که با فاصله جدا شده‌اند:

- "additions"
  - : افزودن گره‌های عنصر (Element Nodes) درون منطقهٔ زنده باید مرتبط در نظر گرفته شود.
- "removals"
  - : حذف گره‌ها از منطقهٔ زنده باید مرتبط در نظر گرفته شود.
- "text"
  - : تغییرات در محتوای متنی گره‌های موجود باید مرتبط در نظر گرفته شود.
- "all"
  - : معادل `"additions removals text"` است.

## مثال‌ها

در این مثال، مقدار `ariaRelevant` روی «all» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRelevant = "all";
  }
  // …
}
```

## سازگاری با مرورگرها

{{Compat}}