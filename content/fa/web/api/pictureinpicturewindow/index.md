---
title: PictureInPictureWindow
slug: Web/API/PictureInPictureWindow
page-type: web-api-interface
browser-compat: api.PictureInPictureWindow
---

{{APIRef("Picture-in-Picture API")}}

رابط **`PictureInPictureWindow`** شیئی را نشان می‌دهد که می‌تواند به صورت برنامه‌نویسی‌شده، **`width`**، **`height`** و **`resize event`** مربوط به پنجرهٔ ویدئوی شناور را در اختیار قرار دهد.

یک شیء با این رابط از طریق مقدار بازگشتی {{domxref("HTMLVideoElement.requestPictureInPicture()")}} که از نوع Promise است به دست می‌آید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_رابط `PictureInPictureWindow` هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("PictureInPictureWindow.width")}} {{ReadOnlyInline}}
  - : عرض پنجرهٔ ویدئوی شناور را تعیین می‌کند.
- {{domxref("PictureInPictureWindow.height")}} {{ReadOnlyInline}}
  - : ارتفاع پنجرهٔ ویدئوی شناور را تعیین می‌کند.

## متدهای نمونه

_رابط `PictureInPictureWindow` هیچ متدی را به ارث نمی‌برد._

## رویدادها

_رابط `PictureInPictureWindow` هیچ رویدادی را به ارث نمی‌برد._

- {{domxref("PictureInPictureWindow.resize_event", "resize")}}
  - : وقتی اندازهٔ پنجرهٔ ویدئوی شناور تغییر کند، به یک `PictureInPictureWindow` ارسال می‌شود.

## مثال‌ها

در مثال زیر، یک `<button>` و یک `<video>` داریم؛ با کلیک روی دکمه، ویدئو وارد حالت تصویر-در-تصویر می‌شود. سپس یک رویداد به آن متصل می‌کنیم تا ابعاد پنجرهٔ شناور ویدئو را در کنسول چاپ کند.

```js
const button = document.querySelector("button");
const video = document.querySelector("video");

function printPipWindowDimensions(evt) {
  const pipWindow = evt.target;
  console.log(
    `The floating window dimensions are: ${pipWindow.width}x${pipWindow.height}px`,
  );
  // will print:
  // The floating window dimensions are: 640x360px
}

button.onclick = () => {
  video.requestPictureInPicture().then((pictureInPictureWindow) => {
    pictureInPictureWindow.onresize = printPipWindowDimensions;
  });
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Picture-in-Picture API](/en-US/docs/Web/API/Picture-in-Picture_API)