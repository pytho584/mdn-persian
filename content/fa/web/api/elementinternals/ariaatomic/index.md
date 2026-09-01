---
title: "ElementInternals: ariaAtomic property"
short-title: ariaAtomic
slug: Web/API/ElementInternals/ariaAtomic
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaAtomic
---

{{APIRef("Web Components")}}

ویژگی **`ariaAtomic`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) است، که نشان می‌دهد آیا فناوری‌های کمکی همهٔ ناحیهٔ تغییر یافته را ارائه می‌دهند یا فقط بخشی از آن را، بر اساس اعلان‌های تغییر تعریف‌شده توسط ویژگی `aria-relevant`.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"false"`
  - : فناوری‌های کمکی فقط گره یا گره‌های تغییر یافته را ارائه می‌دهند.
- `"true"`
  - : فناوری‌های کمکی کل ناحیهٔ تغییر یافته را به‌عنوان یک کل ارائه می‌دهند، از جمله برچسب تعریف‌شده توسط نویسنده در صورت وجود.

## نمونه‌ها

در این مثال، مقدار `ariaAtomic` در سازندهٔ یک عنصر سفارشی روی «true» تنظیم شده است.

```js
class MyCustomElement extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaAtomic = "true";
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}