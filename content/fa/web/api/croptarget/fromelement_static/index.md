```
---
title: "CropTarget: fromElement() static method"
short-title: fromElement()
slug: Web/API/CropTarget/fromElement_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.CropTarget.fromElement_static
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{securecontext_header}}

متد ایستای **`fromElement()`** از رابط {{domxref("CropTarget")}} یک نمونه‌ی `CropTarget` برمی‌گرداند که می‌توان از آن برای برش یک مسیر ویدیویی ضبط‌شده به ناحیه‌ای که یک عنصر مشخص در آن رندر می‌شود استفاده کرد.

از آنجا که Region Capture API یک ناحیه را از تب فعلی مرورگر برش می‌دهد و نه یک عنصر خاص را، هر محتوایی که روی ناحیه‌ی برش‌خورده قرار داشته باشد در ضبط دیده می‌شود.

## نحو

```js-nolint
CropTarget.fromElement(element)
```

### پارامترها

- `element`
  - ارجاعی به یک {{domxref("Element")}} که می‌خواهید به‌عنوان هدف برش از آن استفاده کنید. برای اینکه یک عنصر بتواند به‌عنوان هدف برش استفاده شود، باید:
    - روی صفحه باشد.
    - قابل مشاهده باشد؛ یعنی مثلاً با `display: none` پنهان نشده باشد.

    علاوه بر این، اگر مسیری که قرار است محدود شود دارای کلون باشد (یعنی با {{domxref("BrowserCaptureMediaStreamTrack.clone()")}} ساخته شده باشد) یا ویدیو از تب دیگری غیر از تب فعلی کاربر گرفته شده باشد (مثلاً از طریق {{domxref("Window.postMessage()")}} ارسال شده باشد)، آن عنصر در ضبط قرار نخواهد گرفت.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک نمونه‌ی شیء {{domxref("CropTarget")}} resolve می‌شود؛ سپس می‌توان این نمونه را به {{domxref("BrowserCaptureMediaStreamTrack.CropTo()")}} ارسال کرد تا ویدیوی ضبط‌شده در مسیر، فقط به ناحیه‌ای که عنصر DOM مشخص‌شده در آن رندر می‌شود برش بخورد.

اشیاء `CropTarget` سریال‌پذیر هستند و می‌توان آن‌ها را با سازوکارهایی مانند {{domxref("Window.postMessage()")}} به سند دیگری ارسال کرد.

## مثال‌ها

```js
// Options for getDisplayMedia()
const displayMediaOptions = {
  preferCurrentTab: true,
};

// Create crop target from DOM element
const demoElem = document.querySelector("#demo");
const cropTarget = await CropTarget.fromElement(demoElem);

// Capture video stream from user's webcam and isolate video track
const stream =
  await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
const [track] = stream.getVideoTracks();

// Crop video track
await track.cropTo(cropTarget);

// Broadcast cropped stream in <video> element
videoElem.srcObject = stream;
```

برای مشاهده‌ی مثال‌های کامل در بافت واقعی، به [استفاده از API های Element Capture و Region Capture](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the Element Capture and Region Capture APIs](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)
```