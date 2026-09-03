---
title: "Navigator: presentation property"
short-title: presentation
slug: Web/API/Navigator/presentation
page-type: web-api-instance-property
browser-compat: api.Navigator.presentation
---

{{securecontext_header}}{{APIRef("Presentation API")}}

ویژگی فقط‑خواندنی `presentation` از {{DOMxRef("Navigator")}} به عنوان نقطه ورود برای [Presentation API](/en-US/docs/Web/API/Presentation_API) عمل می‌کند و یک ارجاع به شیء {{DOMxRef("Presentation")}} برمی‌گرداند.

## مقدار

یک ارجاع به شیء {{DOMxRef("Presentation")}}.

## مثال‌ها

در حال حاضر، ویژگی `navigator.presentation` بیشتر برای بررسی وجود ویژگی (feature checking) و در عامل کاربری دریافت‌کننده (receiving user agent) برای دسترسی به {{domxref("PresentationReceiver")}} مفید است.

```js
// Check if the Presentation API is available in the current browser
if ("presentation" in navigator) {
  footer.textContent = navigator.presentation.receiver
    ? "Receiving presentation"
    : "(idle)";
} else {
  console.error("Presentation API is not available in this browser.");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Presentation API](/en-US/docs/Web/API/Presentation_API)
- {{DOMxRef("Presentation")}}