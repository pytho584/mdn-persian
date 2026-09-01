---
title: "HTMLCanvasElement: captureStream() method"
short-title: captureStream()
slug: Web/API/HTMLCanvasElement/captureStream
page-type: web-api-instance-method
browser-compat: api.HTMLCanvasElement.captureStream
---

{{APIRef("Media Capture and Streams")}}

متد **`captureStream()`** از رابط {{domxref("HTMLCanvasElement")}} یک {{domxref("MediaStream")}} برمی‌گرداند که شامل یک {{domxref("CanvasCaptureMediaStreamTrack")}} حاوی ویدئوی زنده از محتویات canvas است.

## نحو (Syntax)

```js-nolint
captureStream()
captureStream(frameRate)
```

### پارامترها

- `frameRate` {{optional_inline}}
  - : یک مقدار اعشاری با دقت مضاعف که نرخ ضبط هر فریم را مشخص می‌کند. اگر تنظیم نشود، هر بار که canvas تغییر کند یک فریم جدید ضبط می‌شود؛ اگر روی `0` تنظیم شود، فریم‌ها به‌طور خودکار ضبط نمی‌شوند و تنها زمانی ضبط می‌شوند که متد {{domxref("CanvasCaptureMediaStreamTrack.requestFrame", "requestFrame()")}} مسیر برگشتی فراخوانی شود.

### مقدار بازگشتی

یک ارجاع به یک شی {{domxref("MediaStream")}} که حاوی یک {{domxref("CanvasCaptureMediaStreamTrack")}} است.

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر مقدار `frameRate` منفی باشد، پرتاب می‌شود.

- `SecurityError` {{domxref("DOMException")}}
  - : بیت‌مپ canvas از نظر مبدأ (origin) تمیز نیست؛ حداقل بخشی از محتویات آن از سایتی غیر از سایتی که سند از آن بارگذاری شده، بارگذاری شده یا ممکن است بارگذاری شده باشد.

## مثال

```js
// یافتن عنصر canvas برای ضبط
const canvasElt = document.querySelector("canvas");

// دریافت جریان (stream)
const stream = canvasElt.captureStream(25); // 25 فریم در ثانیه

// انجام کارهایی با جریان
// مثلاً ارسال آن به کامپیوتر دیگر با استفاده از RTCPeerConnection
//      pc یک RTCPeerConnection است که در جای دیگر ایجاد شده
stream.getTracks().forEach((track) => pc.addTrack(track, stream));
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement.captureStream()")}} که امکان ضبط جریان از یک عنصر رسانه را فراهم می‌کند.
- {{domxref("MediaStream")}}
- [API ضبط و جریان‌های رسانه (Media Capture and Streams API)](/en-US/docs/Web/API/Media_Capture_and_Streams_API)