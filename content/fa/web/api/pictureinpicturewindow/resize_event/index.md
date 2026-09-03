---
title: "PictureInPictureWindow: resize event"
short-title: resize
slug: Web/API/PictureInPictureWindow/resize_event
page-type: web-api-event
browser-compat: api.PictureInPictureWindow.resize_event
---

{{APIRef("Picture-in-Picture API")}}

رویداد **`resize`** زمانی رخ می‌دهد که اندازهٔ پنجرهٔ شناور ویدیو تغییر کرده باشد.

این رویداد لغوپذیر نیست و حباب (bubble) نمی‌کند.

## سینتکس

نام رویداد را در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد را تنظیم کنید.

```js-nolint
addEventListener("resize", (event) => { })

onresize = (event) => { }
```

## نوع رویداد

یک {{domxref("PictureInPictureEvent")}} است و از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("PictureInPictureEvent")}}

## نمونه‌ها

### ثبت‌کنندهٔ اندازهٔ پنجره

```html
<p>Resize the floating video window to fire the <code>resize</code> event.</p>
<p>Window height: <span id="height"></span></p>
<p>Window width: <span id="width"></span></p>
<video id="video" src="" muted autoplay></video>
```

```js
const video = document.querySelector("#video");
const heightOutput = document.querySelector("#height");
const widthOutput = document.querySelector("#width");

function resize(evt) {
  heightOutput.textContent = evt.target.height;
  widthOutput.textContent = evt.target.width;
}

video.requestPictureInPicture().then((pictureInPictureWindow) => {
  pictureInPictureWindow.onresize = resize;
  // or
  pictureInPictureWindow.addEventListener("resize", resize);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
