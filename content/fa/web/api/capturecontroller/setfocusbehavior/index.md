---
title: "CaptureController: setFocusBehavior() method"
short-title: setFocusBehavior()
slug: Web/API/CaptureController/setFocusBehavior
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CaptureController.setFocusBehavior
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متود **`setFocusBehavior()`** از رابط {{domxref("CaptureController")}} کنترل می‌کند که آیا زبانه یا پنجره‌ی ضبط‌شده زمانی که {{jsxref("Promise")}} مربوط به {{domxref("MediaDevices.getDisplayMedia()")}} برآورده می‌شود، فوکوس شود یا اینکه فوکوس روی زبانه‌ای که اپلیکیشن ضبط‌کننده در آن قرار دارد باقی بماند.

شما می‌توانید این رفتار را چندین بار قبل از فراخوانی {{domxref("MediaDevices.getDisplayMedia()")}} یا یک بار بلافاصله پس از حل شدن `Promise` آن تنظیم کنید. پس از آن، رفتار فوکوس نهایی شده تلقی می‌شود و قابل تغییر نیست.

## نحو

```js-nolint
setFocusBehavior(focusBehavior)
```

### پارامترها

- `focusBehavior`
  - : یک مقدار شمارشی که توضیح می‌دهد آیا عامل کاربر باید فوکوس را به سطح نمایش ضبط‌شده منتقل کند یا اپلیکیشن ضبط‌کننده را متمرکز نگه دارد. مقادیر ممکن عبارتند از `focus-captured-surface` (انتقال فوکوس) و `no-focus-change` (حفظ فوکوس روی اپلیکیشن ضبط‌کننده).

### مقدار بازگشتی

هیچ‌کدام (`undefined`).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورت‌های زیر پرتاب می‌شود:
    - جریان ضبط متوقف شده باشد.
    - کاربر به جای یک زبانه یا پنجره‌ی `browser`، یک صفحه‌نمایش (نوع `displaySurface` برابر `monitor`) را برای اشتراک‌گذاری انتخاب کرده باشد – شما نمی‌توانید یک مانیتور را فوکوس کنید. در این حالت، استثنا پس از حل شدن {{jsxref("Promise")}} مربوط به {{domxref("MediaDevices.getDisplayMedia()")}} پرتاب می‌شود.
    - زمان کافی پس از برآورده شدن {{jsxref("Promise")}} مربوط به {{domxref("MediaDevices.getDisplayMedia()")}} سپری شده باشد و رفتار فوکوس نهایی شده باشد.

## مثال‌ها

### استفاده پایه از `setFocusBehavior()`

```js
// Create a new CaptureController instance
const controller = new CaptureController();

// Prompt the user to share a tab, window, or screen.
const stream = await navigator.mediaDevices.getDisplayMedia({ controller });

// Query the displaySurface value of the captured video track
const [track] = stream.getVideoTracks();
const displaySurface = track.getSettings().displaySurface;

if (displaySurface === "browser") {
  // Focus the captured tab.
  controller.setFocusBehavior("focus-captured-surface");
} else if (displaySurface === "window") {
  // Do not move focus to the captured window.
  // Keep the capturing page focused.
  controller.setFocusBehavior("no-focus-change");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [Better screen sharing with Conditional Focus](https://developer.chrome.com/docs/web-platform/conditional-focus/)