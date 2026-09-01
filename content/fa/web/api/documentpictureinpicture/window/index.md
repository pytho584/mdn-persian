---
title: "DocumentPictureInPicture: window property"
short-title: window
slug: Web/API/DocumentPictureInPicture/window
page-type: web-api-instance-property
browser-compat: api.DocumentPictureInPicture.window
---

{{APIRef("Document Picture-in-Picture API")}}{{SecureContext_Header}}

خاصیت فقط‑خواندنی **`window`** در رابط {{domxref("DocumentPictureInPicture")}} یک نمونه از {{domxref("Window")}} را برمی‌گرداند که نمایانگر زمینهٔ مرور درون پنجرهٔ تصویر‑در‑تصویر است.

## مقدار

یک نمونه از شیء {{domxref("Window")}} اگر پنجرهٔ تصویر‑در‑تصویر قبلاً با استفاده از {{domxref("DocumentPictureInPicture.requestWindow()")}} باز شده باشد، در غیر این صورت `null`.

## مثال‌ها

```js
const videoPlayer = document.getElementById("player");

// …

await window.documentPictureInPicture.requestWindow({
  width: videoPlayer.clientWidth,
  height: videoPlayer.clientHeight,
});

// …

const pipWindow = window.documentPictureInPicture.window;
if (pipWindow) {
  // Mute video playing in the Picture-in-Picture window.
  const pipVideo = pipWindow.document.querySelector("#video");
  pipVideo.muted = true;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}}
- [استفاده از Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)