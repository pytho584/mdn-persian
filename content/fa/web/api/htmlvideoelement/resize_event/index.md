---
title: "HTMLVideoElement: resize event"
short-title: resize
slug: Web/API/HTMLVideoElement/resize_event
page-type: web-api-event
browser-compat: api.HTMLVideoElement.resize_event
---

{{APIRef("HTML DOM")}}

رخداد **`resize`** از رابط {{domxref("HTMLVideoElement")}} زمانی فعال می‌شود که یک یا هر دو ویژگی {{domxref("HTMLVideoElement.videoWidth", "videoWidth")}} و {{domxref("HTMLVideoElement.videoHeight", "videoHeight")}} به‌تازگی به‌روزرسانی شده باشند.

این رخداد غیرقابل لغو است اما ممکن است حباب بزند.

## نحو (Syntax)

از نام رخداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رخداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("resize", (event) => { })

onresize = (event) => { }
```

## نوع رخداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```html
<video id="media" src="https://example.com/video.mp4"></video>
```

```js
const el = document.getElementById("media");
el.addEventListener("resize", () => {
  console.log("The size of the video element has changed!");
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLVideoElement.videoHeight")}}
- {{domxref("HTMLVideoElement.videoWidth")}}