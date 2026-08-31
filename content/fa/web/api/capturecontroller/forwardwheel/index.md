---
title: "CaptureController: forwardWheel() method"
short-title: forwardWheel()
slug: Web/API/CaptureController/forwardWheel
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CaptureController.forwardWheel
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`forwardWheel()`** از رابط {{domxref("CaptureController")}} ارسال رویدادهای {{domxref("Element.wheel_event", "wheel")}} (چرخ) که روی عنصر مرجع رخ می‌دهند را به نمای دید (viewport) یک سطح نمایش ضبط‌شده مرتبط آغاز می‌کند.

متد `forwardWheel()` باید از طریق [فعال‌سازی موقت (transient activation)](/en-US/docs/Glossary/Transient_activation) فراخوانی شود. به طور خاص، تنها رویدادهایی که می‌توانند با موفقیت آن را فراخوانی کنند `click` و `input` هستند. همچنین، در اولین تلاش برای ضبط صفحه، از کاربر برای اشتراک‌گذاری زبانه‌ها (tabs) اجازه گرفته می‌شود؛ اگر کاربر اجازه دهد، این شامل اجازه اسکرول کردن زبانه‌های ضبط‌شده نیز می‌شود. اگر مجوز مربوطه از قبل `"granted"` (اعطا شده) باشد، فعال‌سازی موقت نیازی نیست.

## نحو (Syntax)

```js-nolint
forwardWheel(element)
```

### پارامترها

- `element`
  - : ارجاعی به عنصری که رویدادهای `wheel` آن را می‌خواهید به سطح نمایش ضبط‌شده مرتبط ارسال کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} (تعریف‌نشده) تکمیل می‌شود.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که:
    - {{domxref("MediaStream")}} ضبط‌کننده که توسط فراخوانی اصلی {{domxref("MediaDevices.getDisplayMedia()")}} بازگردانده شده، دیگر در حال ضبط نیست، مثلاً به دلیل اینکه روی اشیاء {{domxref("MediaStreamTrack")}} مرتبط متد {{domxref("MediaStreamTrack.stop", "stop()")}} فراخوانی شده است.
    - برنامه در حال ضبط خودش است.
    - تلاشی برای فراخوانی `forwardWheel()` بدون فعال‌سازی موقت انجام شود، در حالی‌که مجوز استفاده از آن توسط کاربر اعطا نشده است.
- `NotAllowedError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که:
    - [سیاست مجوز (Permissions Policy)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) صفحه با هدر {{HTTPHeader("Permissions-Policy/captured-surface-control", "captured-surface-control")}} به صفحه اجازه استفاده از API کنترل سطح ضبط‌شده (Captured Surface Control) را نمی‌دهد.
    - مجوز ضبط سطح نمایش به صراحت توسط کاربر رد شده است.
- `NotSupportedError` {{domxref("DOMException")}}
  - : نوع سطح در حال ضبط یک زبانه مرورگر نیست.

## مثال‌ها

### استفاده پایه از `forwardWheel()`

در نسخه نمایشی زنده ما، که در [استفاده از API کنترل سطح ضبط‌شده (Captured Surface Control)](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control) توضیح داده شده، پس از تکمیل قول (promise) `getDisplayMedia()` ضبط‌کننده، تابعی به نام `startForwarding()` را فراخوانی می‌کنیم:

```js
// Create controller and start capture
const controller = new CaptureController();
videoElem.srcObject = await navigator.mediaDevices.getDisplayMedia({
  controller,
});

// ...

startForwarding();
```

این تابع متد `forwardWheel()` را فراخوانی می‌کند و یک ارجاع به عنصر `<video>` که جریان ضبط‌شده در آن نمایش داده می‌شود، به آن پاس می‌دهد:

```js
async function startForwarding() {
  try {
    await controller.forwardWheel(videoElem);
  } catch (e) {
    console.log(e);
  }
}
```

این باعث می‌شود رویدادهای {{domxref("Element.wheel_event", "wheel")}} (چرخ) که روی عنصر مرجع رخ می‌دهند، به سطح نمایش ضبط‌شده ارسال شوند و به برنامه ضبط‌کننده اجازه اسکرول کردن آن را بدهند.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [استفاده از API کنترل سطح ضبط‌شده (Captured Surface Control)](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)