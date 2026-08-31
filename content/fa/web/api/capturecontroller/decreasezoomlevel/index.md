---
title: "CaptureController: decreaseZoomLevel() method"
short-title: decreaseZoomLevel()
slug: Web/API/CaptureController/decreaseZoomLevel
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CaptureController.decreaseZoomLevel
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

در واسط {{domxref("CaptureController")}}، متد **`decreaseZoomLevel()`** سطح بزرگنمایی (zoom level) سطح نمایشِ در حال ضبط را یک گام کاهش می‌دهد.

متد `decreaseZoomLevel()` باید از طریق [فعال‌سازی گذرا](/en-US/docs/Glossary/Transient_activation) فراخوانی شود. علاوه بر این، هنگام اولین تلاش برای ضبط صفحه، از کاربر برای اشتراک‌گذاری تب‌ها اجازه خواسته می‌شود؛ اگر کاربر اجازه را رد کند، حتی با فعال‌سازی گذرا نیز نمی‌توان سطح بزرگنمایی را تغییر داد.

## نحو (Syntax)

```js-nolint
decreaseZoomLevel()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} برآورده (fulfill) می‌شود.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : در این موارد پرتاب می‌شود:
    - سطح نمایشِ در حال ضبط از قبل در کمترین سطح بزرگنمایی پشتیبانی‌شده قرار دارد.
    - تلاش برای فراخوانی `decreaseZoomLevel()` بدون فعال‌سازی گذرا انجام شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در این موارد پرتاب می‌شود:
    - [سیاست مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) صفحه، یعنی {{HTTPHeader("Permissions-Policy/captured-surface-control", "captured-surface-control")}}، به صفحه اجازه استفاده از API کنترل سطح ضبط‌شده (Captured Surface Control API) را نمی‌دهد.
    - اجازه ضبط سطح نمایش به‌صراحت توسط کاربر رد شود.

## مثال‌ها

### استفاده پایه از `decreaseZoomLevel()`

قطعه کد زیر یک شنونده رویداد به یک دکمه اضافه می‌کند تا وقتی روی آن کلیک شد، تابع `decreaseZoom()` فراخوانی شود. این تابع به نوبه خود متد `decreaseZoomLevel()` را فراخوانی کرده و سطح بزرگنمایی سطح ضبط‌شده را کاهش می‌دهد.

```js
// Create controller and start capture
const controller = new CaptureController();
videoElem.srcObject = await navigator.mediaDevices.getDisplayMedia({
  controller,
});

// ...

decBtn.addEventListener("click", decreaseZoom);

async function decreaseZoom() {
  try {
    await controller.decreaseZoomLevel();
  } catch (e) {
    console.log(e);
  }
}
```

معمولاً بهترین روش این است که `decreaseZoomLevel()` را درون یک بلوک [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) فراخوانی کنید، زیرا ممکن است سطح بزرگنمایی به‌صورت ناهمگام توسط موجودیتی غیر از برنامه تغییر کند و این امر منجر به پرتاب خطا شود. برای مثال، کاربر ممکن است مستقیماً با سطح ضبط‌شده تعامل کند تا بزرگنمایی را افزایش یا کاهش دهد.

برای یک مثال کامل و عملی، به [استفاده از API کنترل سطح ضبط‌شده](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [استفاده از API کنترل سطح ضبط‌شده](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)
