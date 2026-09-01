---
title: "ElementInternals: ariaLive property"
short-title: ariaLive
slug: Web/API/ElementInternals/ariaLive
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaLive
---

{{APIRef("Web Components")}}

ویژگی **`ariaLive`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) را منعکس می‌کند. این ویژگی نشان می‌دهد که یک عنصر به‌روزرسانی خواهد شد و انواع به‌روزرسانی‌هایی را که عامل‌های کاربر، فناوری‌های کمکی و کاربر می‌توانند از ناحیه زنده (live region) انتظار داشته باشند، توصیف می‌کند.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما اطمینان حاصل می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکرده باشد، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"assertive"` (مصمم)
  - : نشان می‌دهد که به‌روزرسانی‌های ناحیه بالاترین اولویت را دارند و باید فوراً به کاربر ارائه شوند.
- `"off"` (خاموش)
  - : نشان می‌دهد که به‌روزرسانی‌های ناحیه نباید به کاربر ارائه شوند، مگر اینکه کاربر در حال حاضر روی آن ناحیه تمرکز داشته باشد.
- `"polite"` (مؤدبانه)
  - : نشان می‌دهد که به‌روزرسانی‌های ناحیه باید در نخستین فرصت مناسب ارائه شوند، مانند پایان جمله فعلی یا زمانی که کاربر تایپ را متوقف می‌کند.

## مثال‌ها

در این مثال، مقدار `ariaLive` روی `"assertive"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaLive = "assertive";
  }
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}