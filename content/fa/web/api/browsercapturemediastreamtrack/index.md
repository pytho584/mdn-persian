---
title: "BrowserCaptureMediaStreamTrack"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BrowserCaptureMediaStreamTrack"
translated_by: "n8n + AI"
---

---
title: BrowserCaptureMediaStreamTrack
slug: Web/API/BrowserCaptureMediaStreamTrack
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BrowserCaptureMediaStreamTrack
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}

رابط **`BrowserCaptureMediaStreamTrack`** از {{domxref("Screen Capture API", "Screen Capture API", "", "nocode")}} یک ترک ویدیویی واحد را نمایش می‌دهد. این رابط کلاس {{domxref("MediaStreamTrack")}} را با متدهایی برای محدود کردن بخشی از جریان خود-ضبط (مثلاً صفحه یا پنجره کاربر) که ضبط می‌شود، گسترش می‌دهد.

{{InheritanceDiagram}}

## متدهای نمونه

- {{domxref("BrowserCaptureMediaStreamTrack.clone", "clone()")}} {{Experimental_Inline}}
  - : یک کلون بدون برش و بدون محدودیت از `BrowserCaptureMediaStreamTrack` اصلی بازمی‌گرداند.
- {{domxref("BrowserCaptureMediaStreamTrack.cropTo", "cropTo()")}} {{Experimental_Inline}}
  - : یک جریان خود-ضبط را به ناحیه‌ای که یک عنصر DOM مشخص در آن رندر شده است، برش می‌دهد.
- {{domxref("BrowserCaptureMediaStreamTrack.restrictTo", "restrictTo()")}} {{Experimental_Inline}}
  - : یک جریان خود-ضبط را به یک عنصر DOM خاص محدود می‌کند.

## مثال‌ها

برای مشاهده کد نمونه در بافتار، [استفاده از APIهای Element Capture و Region Capture](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از APIهای Element Capture و Region Capture](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)