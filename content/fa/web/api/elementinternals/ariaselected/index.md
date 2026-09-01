---
title: "ElementInternals: ariaSelected property"
---

---
title: "ElementInternals: ariaSelected property"
short-title: ariaSelected
slug: Web/API/ElementInternals/ariaSelected
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaSelected
---

{{APIRef("Web Components")}}

ویژگی **`ariaSelected`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) است، که وضعیت «انتخاب‌شده» فعلی عناصری را نشان می‌دهد که حالت انتخاب دارند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی می‌دهد. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اطمینان حاصل می‌کنند که در صورت حذف آن ویژگی‌ها توسط نویسنده یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : مورد انتخاب شده است.
- `"false"`
  - : مورد انتخاب نشده است.
- `"undefined"`
  - : مورد انتخاب نشده است.

## مثال‌ها

در این مثال، مقدار `ariaSelected` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaSelected = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش tab](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)