---
title: CaptureController
slug: Web/API/CaptureController
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CaptureController
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابطهٔ **`CaptureController`** روش‌هایی را فراهم می‌کند که می‌توان از آن‌ها برای دستکاری بیشتر سطح نمایشِ ضبط‌شده (که از طریق {{domxref("MediaDevices.getDisplayMedia()")}} ضبط شده است) استفاده کرد.

یک شیء `CaptureController` با ارسال آن به فراخوانی `getDisplayMedia()` به‌عنوان مقدار ویژگی `controller` در شیء گزینه‌ها، با سطح نمایش ضبط‌شده مرتبط می‌شود.

## سازنده

- {{ domxref("CaptureController.CaptureController", "CaptureController()") }} {{Experimental_Inline}}
  - : یک نمونهٔ جدید از شیء `CaptureController` می‌سازد.

## ویژگی‌های نمونه

- {{ domxref("CaptureController.zoomLevel", "zoomLevel") }} {{Experimental_Inline}}
  - : سطح زوم فعلی سطح نمایش ضبط‌شده.

## روش‌های نمونه

- {{ domxref("CaptureController.decreaseZoomLevel", "decreaseZoomLevel()") }} {{Experimental_Inline}}
  - : سطح زوم سطح نمایش ضبط‌شده را به‌اندازهٔ یک پله کاهش می‌دهد.
- {{ domxref("CaptureController.forwardWheel", "forwardWheel()") }} {{Experimental_Inline}}
  - : شروع به ارسال رویدادهای {{domxref("Element.wheel_event", "wheel")}} می‌کند که روی عنصر ارجاع‌داده‌شده رخ می‌دهند به viewport سطح نمایش ضبط‌شدهٔ مرتبط.
- {{ domxref("CaptureController.getSupportedZoomLevels", "getSupportedZoomLevels()") }} {{Experimental_Inline}}
  - : سطوح زوم مختلف پشتیبانی‌شده توسط سطح نمایش ضبط‌شده را برمی‌گرداند.
- {{ domxref("CaptureController.increaseZoomLevel", "increaseZoomLevel()") }} {{Experimental_Inline}}
  - : سطح زوم سطح نمایش ضبط‌شده را به‌اندازهٔ یک پله افزایش می‌دهد.
- {{ domxref("CaptureController.resetZoomLevel", "resetZoomLevel()") }} {{Experimental_Inline}}
  - : زوم سطح نمایش ضبط‌شده را به سطح اولیهٔ آن یعنی `100` بازنشانی می‌کند.
- {{ domxref("CaptureController.setFocusBehavior", "setFocusBehavior()") }} {{Experimental_Inline}}
  - : کنترل می‌کند که آیا تب یا پنجرهٔ ضبط‌شده فوکوس شود یا فوکوس در تب حاوی برنامهٔ ضبط‌کننده باقی بماند.

## رویدادها

- {{ domxref("CaptureController.zoomlevelchange_event", "zoomlevelchange") }} {{Experimental_Inline}}
  - : زمانی که سطح زوم سطح نمایش ضبط‌شده تغییر می‌کند، رخ می‌دهد.

## مثال‌ها

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [Using the Element Capture and Region Capture APIs](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)
- [Using the Captured Surface Control API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)
- [Better screen sharing with Conditional Focus](https://developer.chrome.com/docs/web-platform/conditional-focus/)