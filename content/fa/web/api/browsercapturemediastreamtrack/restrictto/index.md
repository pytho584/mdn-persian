---
title: "BrowserCaptureMediaStreamTrack: restrictTo() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BrowserCaptureMediaStreamTrack/restrictTo"
translated_by: "n8n + AI"
---

---
title: "BrowserCaptureMediaStreamTrack: restrictTo() method"
short-title: restrictTo()
slug: Web/API/BrowserCaptureMediaStreamTrack/restrictTo
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BrowserCaptureMediaStreamTrack.restrictTo
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`restrictTo()`** در رابط {{domxref("BrowserCaptureMediaStreamTrack")}} جریان خودگیری را به یک عنصر DOM خاص (و فرزندان آن) محدود میکند.

## نحو

```js-nolint
restrictTo(restrictionTarget)
```

### پارامترها

- `restrictionTarget`
  - : یک نمونه {{domxref("RestrictionTarget")}} که عنصری را نشان میدهد که جریان باید به آن محدود شود، یا `null`/`undefined`، که در این صورت هر محدودیت قبلی از روی ترک برداشته میشود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{jsxref("undefined")}} تبدیل میشود.

Promise رد میشود اگر:

- [`kind`](/en-US/docs/Web/API/MediaStreamTrack/kind) ترک `"video"` نباشد، یا [`readyState`](/en-US/docs/Web/API/MediaStreamTrack/readyState) آن `"live"` نباشد.
- عنصر هدف محدودسازی دیگر وجود نداشته باشد.
- ترکی که محدود میشود، ترکی نباشد که از صفحه کاربر ضبط شده است.
- `restrictionTarget` نمونهای از {{domxref("RestrictionTarget")}}، `null` یا `undefined` نباشد.
- `restrictionTarget` در تب دیگری غیر از تبی که در حال ضبط است ساخته شده باشد.

> [!NOTE]
> در کرومیوم، اگر یک ترک کلون داشته باشد، `restrictTo()` رد میشود (به [Chrome issue 41482026](https://crbug.com/41482026) مراجعه کنید).

## مثالها

### مثال پایه محدودسازی

```js
// Options for getDisplayMedia()
const displayMediaOptions = {
  preferCurrentTab: true,
};

// Create restriction target from DOM element
const demoElem = document.querySelector("#demo");
const restrictionTarget = await RestrictionTarget.fromElement(demoElem);

// Capture video stream from user's webcam and isolate video track
const stream =
  await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
const [track] = stream.getVideoTracks();

// Restrict video track
await track.restrictTo(restrictionTarget);

// Broadcast restricted stream in <video> element
videoElem.srcObject = stream;
```

برای مثال کد در متن، به [Using the Element Capture and Region Capture APIs](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture) مراجعه کنید.

### توقف محدودسازی

میتوانید با فراخوانی `restrictTo()` روی همان ترک و ارسال آرگومان `null` به آن، محدودسازی را متوقف کنید:

```js
// Stop restricting
await track.restrictTo(null);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the Element Capture and Region Capture APIs](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)