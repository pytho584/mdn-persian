---
title: "ElementInternals: ariaRequired property"
short-title: ariaRequired
slug: Web/API/ElementInternals/ariaRequired
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaRequired
---

{{APIRef("Web Components")}}

ویژگی **`ariaRequired`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده مقدار ویژگی [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required) است که نشان می‌دهد آیا ورودی کاربر قبل از ارسال فرم الزامی است یا خیر.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این مقادیر ممکن است توسط ویژگی‌های تعریف‌شده توسط مؤلف بازنویسی شوند، اما تضمین می‌کنند که در صورت حذف آن ویژگی‌ها توسط مؤلف یا عدم افزودن آن‌ها، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهنده مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : کاربران باید قبل از ارسال فرم، ورودی را روی عنصر ارائه دهند.
- `"false"`
  - : ورودی کاربر برای ارسال فرم ضروری نیست.

## مثال‌ها

در این مثال، مقدار `ariaRequired` روی «true» تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaRequired = "true";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)