---
title: "CaptureController: resetZoomLevel() method"
short-title: resetZoomLevel()
slug: Web/API/CaptureController/resetZoomLevel
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CaptureController.resetZoomLevel
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`resetZoomLevel()`** در رابط {{domxref("CaptureController")}}، سطح بزرگنمایی (zoom) سطح نمایشِ در حال ضبط را به مقدار اولیهٔ آن، یعنی `100` بازنشانی می‌کند.

متد `resetZoomLevel()` باید از طریق [فعال‌سازی گذرا (transient activation)](/en-US/docs/Glossary/Transient_activation) فراخوانی شود. علاوه بر این، هنگام اولین تلاش برای ضبط صفحه، از کاربر برای به اشتراک‌گذاری تب‌ها اجازه گرفته می‌شود؛ اگر کاربر اجازه را رد کند، حتی با فعال‌سازی گذرا نیز نمی‌توان سطح بزرگنمایی را تغییر داد.

## Syntax

```js-nolint
resetZoomLevel()
```

### Parameters

هیچ‌کدام.

### Return value

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} انجام می‌شود (fulfill).

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که تلاش شود `resetZoomLevel()` بدون فعال‌سازی گذرا فراخوانی شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در شرایط زیر پرتاب می‌شود:
    - [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) صفحه، با هدر {{HTTPHeader("Permissions-Policy/captured-surface-control", "captured-surface-control")}} به صفحه اجازهٔ استفاده از Captured Surface Control API را ندهد.
    - اجازهٔ ضبط سطح نمایش به‌صراحت توسط کاربر رد شده باشد.

## Examples

### استفادهٔ پایه از `resetZoomLevel()`

قطعهٔ کد زیر یک شنوندهٔ رویداد به یک دکمه اضافه می‌کند تا وقتی روی آن کلیک شد، تابع `resetZoom()` فراخوانی شود. این تابع نیز به نوبهٔ خود متد `resetZoomLevel()` را فراخوانی می‌کند و سطح بزرگنمایی سطحِ ضبط‌شده را به `100` بازنشانی می‌کند.

```js
// Create controller and start capture
const controller = new CaptureController();
videoElem.srcObject = await navigator.mediaDevices.getDisplayMedia({
  controller,
});

// ...

resetBtn.addEventListener("click", resetZoom);

async function resetZoom() {
  await controller.resetZoomLevel();
}
```

برای مشاهدهٔ یک مثال کامل و کاربردی، به [استفاده از Captured Surface Control API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [استفاده از Captured Surface Control API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)