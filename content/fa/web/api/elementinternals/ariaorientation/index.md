---
title: "ElementInternals: ariaOrientation property"
short-title: ariaOrientation
slug: Web/API/ElementInternals/ariaOrientation
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaOrientation
---

{{APIRef("Web Components")}}

خاصیت **`ariaOrientation`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) را منعکس می‌کند؛ این ویژگی نشان می‌دهد که جهت عنصر افقی، عمودی یا نامشخص/مبهم است.

> [!NOTE]
> تنظیم ویژگی‌های aria بر روی `ElementInternals` امکان تعریف معنای پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. ممکن است این مقادیر توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معنای پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل اشیاء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"horizontal"`
  - : عنصر افقی است.
- `"vertical"`
  - : عنصر عمودی است.
- `"undefined"`
  - : جهت عنصر نامشخص است.

## مثال‌ها

در این مثال مقدار `ariaOrientation` روی «vertical» تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaOrientation = "vertical";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}