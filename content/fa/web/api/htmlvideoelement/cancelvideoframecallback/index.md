---
title: "HTMLVideoElement: cancelVideoFrameCallback() method"
short-title: cancelVideoFrameCallback()
slug: Web/API/HTMLVideoElement/cancelVideoFrameCallback
page-type: web-api-instance-method
browser-compat: api.HTMLVideoElement.cancelVideoFrameCallback
---

{{APIRef("HTML DOM")}}

متد **`cancelVideoFrameCallback()`** از رابط {{domxref("HTMLVideoElement")}} فراخوان فریم ویدیویی را که قبلاً ثبت شده است لغو می‌کند.

## سینتکس

```js-nolint
cancelVideoFrameCallback(id)
```

### پارامترها

- `id`
  - : عددی که شناسهٔ فراخوان فریم ویدیویی موردنظر برای لغو را نشان می‌دهد. این مقدار، همان مقداری است که توسط فراخوان متناظر {{DOMxRef("HTMLVideoElement.requestVideoFrameCallback")}} بازگردانده شده است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### لغو یک فراخوان فریم ویدیویی

این مثال نشان می‌دهد که چگونه می‌توان با استفاده از `cancelVideoFrameCallback()` یک فراخوان فریم ویدیوییِ قبلاً ثبت‌شده را لغو کرد.

```js
let videoCallbackId = null;

function updateCanvas(now, metadata) {
  // Do something with the frame

  // …

  // Re-register the callback to run on the next frame
  // It's important to update the videoCallbackId on each iteration
  // so you can cancel the callback successfully
  videoCallbackId = video.requestVideoFrameCallback(updateCanvas);
}

// Initial registration of the callback to run on the first frame
videoCallbackId = video.requestVideoFrameCallback(updateCanvas);

// …

// Cancel video frame callback using the latest videoCallbackId
if (videoCallbackId !== null) {
  video.cancelVideoFrameCallback(videoCallbackId);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("video")}}
- {{DOMxRef("HTMLVideoElement.requestVideoFrameCallback()")}}
- [انجام عملیات کارآمد به ازای هر فریم ویدیو با `requestVideoFrameCallback()`](https://web.dev/articles/requestvideoframecallback-rvfc) در developer.chrome.com (2023)