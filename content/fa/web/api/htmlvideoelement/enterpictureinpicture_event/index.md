```
---
title: "HTMLVideoElement: enterpictureinpicture event"
---

---
title: "HTMLVideoElement: enterpictureinpicture event"
short-title: enterpictureinpicture
slug: Web/API/HTMLVideoElement/enterpictureinpicture_event
page-type: web-api-event
browser-compat: api.HTMLVideoElement.enterpictureinpicture_event
---

{{APIRef("Picture-in-Picture API")}}

رویداد `enterpictureinpicture` زمانی فعال می‌شود که {{DOMxRef("HTMLVideoElement")}} با موفقیت وارد حالت تصویر-در-تصویر شود.

این رویداد قابل لغو (cancelable) نیست و bubble نمی‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("enterpictureinpicture", (event) => { })

onenterpictureinpicture = (event) => { }
```

## نوع رویداد

یک {{domxref("PictureInPictureEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PictureInPictureEvent")}}

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `enterpictureinpicture` عنصر HTMLVideoElement اضافه می‌کنند و سپس هنگامی که آن کنترل‌کننده رویداد به فعال شدن رویداد واکنش نشان داد، یک پیام ارسال می‌کنند.

با استفاده از `addEventListener()`:

```js
const video = document.querySelector("#video");
const button = document.querySelector("#button");

function onEnterPip() {
  console.log("Picture-in-Picture mode activated!");
}

video.addEventListener("enterpictureinpicture", onEnterPip);

button.onclick = () => {
  video.requestPictureInPicture();
};
```

با استفاده از ویژگی کنترل‌کننده رویداد `onenterpictureinpicture`:

```js
const video = document.querySelector("#video");
const button = document.querySelector("#button");

function onEnterPip() {
  console.log("Picture-in-Picture mode activated!");
}

video.onenterpictureinpicture = onEnterPip;

button.onclick = () => {
  video.requestPictureInPicture();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLVideoElement")}}
- [Picture-in-Picture API](/en-US/docs/Web/API/Picture-in-Picture_API)
```