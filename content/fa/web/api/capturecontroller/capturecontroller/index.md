---
title: "CaptureController: CaptureController() constructor"
short-title: CaptureController()
slug: Web/API/CaptureController/CaptureController
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CaptureController.CaptureController
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

سازندهٔ {{domxref("CaptureController")}} یک نمونه شیء جدید از `CaptureController` ایجاد می‌کند.

## دستور زبان

```js-nolint
CaptureController()
```

### پارامترها

هیچ.

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

## جستارهای وابسته

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [Better screen sharing with Conditional Focus](https://developer.chrome.com/docs/web-platform/conditional-focus/)