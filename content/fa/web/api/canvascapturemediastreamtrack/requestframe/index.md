---
title: "CanvasCaptureMediaStreamTrack: requestFrame() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanvasCaptureMediaStreamTrack/requestFrame"
translated_by: "n8n + AI"
---

---
title: "CanvasCaptureMediaStreamTrack: requestFrame() method"
short-title: requestFrame()
slug: Web/API/CanvasCaptureMediaStreamTrack/requestFrame
page-type: web-api-instance-method
browser-compat: api.CanvasCaptureMediaStreamTrack.requestFrame
---

{{APIRef("Media Capture and Streams")}}

متد **`requestFrame()`** از رابط {{domxref("CanvasCaptureMediaStreamTrack")}} درخواست می‌کند که یک فریم از بوم گرفته شود و به جریان ارسال شود.

برنامه‌هایی که نیاز به کنترل دقیق زمان‌بندی رندر و ضبط فریم دارند، می‌توانند برای مشخص کردن مستقیم زمان مناسب ضبط یک فریم، از `requestFrame()` استفاده کنند.

برای جلوگیری از ضبط خودکار فریم‌ها، به‌طوری که فریم‌ها فقط زمانی که `requestFrame()` فراخوانی می‌شود ضبط شوند، هنگام ایجاد جریان، مقدار 0 را برای متد {{domxref("HTMLCanvasElement.captureStream", "captureStream()")}} مشخص کنید.

## نحو

```js-nolint
requestFrame()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## یادداشت‌های استفاده

در حال حاضر یک مشکل در مشخصات علامت‌گذاری شده است که اشاره می‌کند در این زمان، اگر بوم از نظر مبدأ پاک (origin-clean) نباشد، هیچ استثنایی پرتاب نمی‌شود. این ممکن است در آینده تغییر کند؛ بنابراین عاقلانه است که از قبل برنامه‌ریزی کرده و مراقب استثناهایی مانند `SecurityError` باشید (اگرچه خطای خاصی که ممکن است پرتاب شود در مشخصات ذکر نشده است، اما این یک گزینه محتمل است).

## مثال

```js
// Find the canvas element to capture
const canvasElt = document.querySelector("canvas");

// Get the stream
const stream = canvasElt.captureStream(25); // 25 FPS

// Send the current state of the canvas as a frame to the stream
stream.getVideoTracks()[0].requestFrame();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasCaptureMediaStreamTrack")}}، رابطی که این متد به آن تعلق دارد.
- {{HTMLElement("canvas")}}