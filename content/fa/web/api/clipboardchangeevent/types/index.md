---
title: "ClipboardChangeEvent: types property"
short-title: types
slug: Web/API/ClipboardChangeEvent/types
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ClipboardChangeEvent.types
---

{{securecontext_header}}{{APIRef("Clipboard API")}}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`types`** از رابط {{domxref("ClipboardChangeEvent")}}، آرایه‌ای از رشته‌ها را برمی‌گرداند که نشان‌دهندهٔ {{glossary("MIME type","انواع MIME")}} اجباری موجود در حافظهٔ موقت (clipboard) سیستم در زمان رخداد `ClipboardChangeEvent` هستند. انواع اختیاری و قالب‌های سفارشی برای محدود کردن {{glossary("fingerprinting","اثر انگشت‌گذاری")}} در این آرایه گنجانده نشده‌اند.

## مقدار

آرایه‌ای از رشته‌ها.

## مثال‌ها

در این مثال، هنگامی که محتوای حافظهٔ موقت تغییر می‌کند، شنوندهٔ رویداد هر رشته‌ای را که نشان‌دهندهٔ یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) است و در آرایهٔ بازگشتی از ویژگی `ClipboardChangeEvent.types` موجود است، در کنسول ثبت می‌کند.

```js
navigator.clipboard.addEventListener("clipboardchange", (event) => {
  event.types.forEach((value) => {
    console.log(value);
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ClipboardChangeEvent.changeId")}}
- {{domxref("ClipboardChangeEvent")}}
- {{domxref("ClipboardEvent")}}
- [API حافظهٔ موقت](/en-US/docs/Web/API/Clipboard_API)