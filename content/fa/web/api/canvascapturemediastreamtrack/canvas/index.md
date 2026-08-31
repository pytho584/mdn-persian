---
title: "CanvasCaptureMediaStreamTrack: canvas property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanvasCaptureMediaStreamTrack/canvas"
translated_by: "n8n + AI"
---

---
title: "CanvasCaptureMediaStreamTrack: canvas property"
short-title: canvas
slug: Web/API/CanvasCaptureMediaStreamTrack/canvas
page-type: web-api-instance-property
browser-compat: api.CanvasCaptureMediaStreamTrack.canvas
---

{{APIRef("Media Capture and Streams")}}

ویژگی فقط‌خواندنی **`canvas`** از رابط {{domxref("CanvasCaptureMediaStreamTrack")}} عنصر {{domxref("HTMLCanvasElement")}} را که فریم‌ها از آن گرفته می‌شوند برمی‌گرداند.

## مقدار

یک `HTMLCanvasElement` که بوم را نشان می‌دهد و منبع فریم‌های در حال ضبط است.

## مثال

```js
// Find the canvas element to capture
const canvasElt = document.querySelector("canvas");

// Get the stream
const stream = canvasElt.captureStream(25); // 25 FPS

// Do things to the stream
// …

// Obtain the canvas associated with the stream
const canvas = stream.canvas;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.captureStream()")}} برای ایجاد یک جریان برای ضبط یک عنصر بوم معین.
- {{HTMLElement("canvas")}}