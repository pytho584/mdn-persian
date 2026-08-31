---
title: "CaptureController: increaseZoomLevel() method"
short-title: increaseZoomLevel()
slug: Web/API/CaptureController/increaseZoomLevel
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CaptureController.increaseZoomLevel
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

در رابط {{domxref("CaptureController")}}، متد **`increaseZoomLevel()`** سطح بزرگ‌نمایی سطح نمایشِ در حال ضبط را به اندازه یک پله افزایش می‌دهد.

متد `increaseZoomLevel()` باید از طریق [فعال‌سازی گذرا](/en-US/docs/Glossary/Transient_activation) فراخوانی شود. علاوه بر این، هنگام اولین تلاش برای ضبط صفحه، از کاربر برای اشتراک‌گذاری برگه‌ها اجازه گرفته می‌شود؛ اگر کاربر اجازه ندهد، حتی با فعال‌سازی گذرا نیز نمی‌توان سطح بزرگ‌نمایی را تغییر داد.

## نحو (Syntax)

```js-nolint
increaseZoomLevel()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} تمام می‌شود.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - سطح نمایشِ در حال ضبط از قبل در حداکثر سطح بزرگ‌نمایی پشتیبانی‌شده قرار دارد.
    - تلاش برای فراخوانی `increaseZoomLevel()` بدون فعال‌سازی گذرا انجام شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - [خط مشی مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) صفحه با هدر {{HTTPHeader("Permissions-Policy/captured-surface-control", "captured-surface-control")}} به صفحه اجازه استفاده از API کنترل سطح ضبط‌شده (Captured Surface Control API) را ندهد.
    - اجازه ضبط سطح نمایش به‌صراحت توسط کاربر رد شده باشد.

## مثال‌ها

### استفاده پایه از `increaseZoomLevel()`

قطعه کد زیر یک شنونده رویداد به یک دکمه اضافه می‌کند که با کلیک روی آن، تابع `increaseZoom` فراخوانی می‌شود. این تابع به نوبه خود متد `increaseZoomLevel()` را فراخوانی کرده و سطح بزرگ‌نمایی سطحِ در حال ضبط را افزایش می‌دهد.

```js
// Create controller and start capture
const controller = new CaptureController();
videoElem.srcObject = await navigator.mediaDevices.getDisplayMedia({
  controller,
});

// ...

incBtn.addEventListener("click", increaseZoom);

async function increaseZoom() {
  try {
    await controller.increaseZoomLevel();
  } catch (e) {
    console.log(e);
  }
}
```

به‌طور کلی بهتر است `increaseZoomLevel()` را درون یک بلوک [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) فراخوانی کنید، زیرا ممکن است سطح بزرگ‌نمایی به‌صورت ناهمگام توسط موجودیتی غیر از برنامه تغییر کند و این امر منجر به پرتاب خطا شود. برای مثال، کاربر ممکن است مستقیماً با سطحِ در حال ضبط تعامل کند تا بزرگ‌نمایی را افزایش یا کاهش دهد.

برای مشاهده یک مثال کامل و کاربردی، به [استفاده از API کنترل سطح ضبط‌شده](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [استفاده از API کنترل سطح ضبط‌شده](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)