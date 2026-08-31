---
title: "CaptureController: zoomlevelchange event"
---

---
title: "CaptureController: zoomlevelchange event"
short-title: zoomlevelchange
slug: Web/API/CaptureController/zoomlevelchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.CaptureController.zoomlevelchange_event
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}

هنگامی که سطح بزرگنمایی سطح نمایش ضبط‌شده تغییر کند، رویداد **`zoomlevelchange`** از رابط {{domxref("CaptureController")}} فعال می‌شود.

این رویداد به‌طور خاص در موارد زیر رخ می‌دهد:

- متدهای {{domxref("CaptureController.increaseZoomLevel", "increaseZoomLevel()")}}، {{domxref("CaptureController.decreaseZoomLevel", "decreaseZoomLevel()")}}، یا {{domxref("CaptureController.resetZoomLevel", "resetZoomLevel()")}} روی کنترل‌کننده‌ای که به‌طور فعال در حال کنترل سطح نمایش ضبط‌شده است، فراخوانی شوند.
- کاربر سطح بزرگنمایی را در سطح ضبط‌شده تغییر دهد.
- کاربر سطح نمایش ضبط‌شده را به سطح دیگری با سطح بزرگنمایی متفاوت تغییر دهد.

## دستور زبان

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("zoomlevelchange", (event) => { })

onzoomlevelchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### استفاده پایه از `zoomlevelchange`

هنگامی که سطح بزرگنمایی سطح نمایش ضبط‌شده تغییر می‌کند، یک رویداد `zoomlevelchange` روی کنترل‌کننده فعال می‌شود که می‌توان از آن برای اجرای یک کنترل‌کننده رویداد مانند نمونه زیر استفاده کرد. این کار، سطح بزرگنمایی به‌روز شده را در یک عنصر خروجی می‌نویسد.

```js
// Create controller and start capture
const controller = new CaptureController();
videoElem.srcObject = await navigator.mediaDevices.getDisplayMedia({
  controller,
});

// ...

controller.addEventListener(
  "zoomlevelchange",
  () => (outputElem.textContent = `${controller.zoomLevel}%`),
);
```

برای یک مثال کامل و قابل اجرا، به [Using the Captured Surface Control API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [Using the Captured Surface Control API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)