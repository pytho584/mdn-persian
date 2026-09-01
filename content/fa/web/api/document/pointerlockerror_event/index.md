---
title: "Document: pointerlockerror event"
short-title: pointerlockerror
slug: Web/API/Document/pointerlockerror_event
page-type: web-api-event
browser-compat: api.Document.pointerlockerror_event
---

{{APIRef("Pointer Lock API")}}

رویداد **`pointerlockerror`** زمانی رخ می‌دهد که قفل کردن نشانگر (pointer) ناموفق باشد (به دلایل فنی یا به دلیل رد شدن مجوز).

این رویداد قابل لغو (cancelable) نیست و حباب (bubble) نمی‌زند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerlockerror", (event) => { })

onpointerlockerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

document.addEventListener("pointerlockerror", (event) => {
  console.log("Error locking pointer");
});
```

استفاده از ویژگی کنترل‌کننده رویداد `onpointerlockerror`:

```js
document.onpointerlockerror = (event) => {
  console.log("Error locking pointer");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Pointer Lock API](/en-US/docs/Web/API/Pointer_Lock_API)