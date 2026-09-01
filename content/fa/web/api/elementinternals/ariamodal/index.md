---
title: "ElementInternals: ariaModal property"
short-title: ariaModal
slug: Web/API/ElementInternals/ariaModal
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaModal
---

{{APIRef("Web Components")}}

ویژگی **`ariaModal`** از رابط {{domxref("ElementInternals")}}، مقدار ویژگی [`aria-modal`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-modal) را منعکس می‌کند؛ ویژگی‌ای که مشخص می‌کند آیا یک عنصر هنگام نمایش، وجهی (modal) است یا خیر.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. ممکن است این مقادیر توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً اضافه نکند، معناشناسی پیش‌فرض حفظ می‌شود. برای اطلاعات بیشتر به [توضیح‌دهنده (explainer) مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته (string) با یکی از مقادیر زیر:

- `"true"`
  - : عنصر وجهی (modal) است.
- `"false"`
  - : عنصر وجهی (modal) نیست.

## مثال‌ها

در این مثال، مقدار `ariaModal` برابر `"true"` تنظیم شده است.

```js
class CustomEl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaModal = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: dialog role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)
