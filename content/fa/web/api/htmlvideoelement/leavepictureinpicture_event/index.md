---
title: "HTMLVideoElement: leavepictureinpicture event"
---

---
title: "HTMLVideoElement: leavepictureinpicture event"
short-title: leavepictureinpicture
slug: Web/API/HTMLVideoElement/leavepictureinpicture_event
page-type: web-api-event
browser-compat: api.HTMLVideoElement.leavepictureinpicture_event
---

{{APIRef("Picture-in-Picture API")}}

رویداد `leavepictureinpicture` زمانی فعال می‌شود که {{DOMxRef("HTMLVideoElement")}} با موفقیت از حالت تصویر-در-تصویر خارج شود.

این رویداد قابل‌لغو نیست و حباب نمی‌کند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("leavepictureinpicture", (event) => { })

onleavepictureinpicture = (event) => { }
```

## نوع رویداد

یک {{domxref("PictureInPictureEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PictureInPictureEvent")}}

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `leavepictureinpicture` عنصر HTMLVideoElement اضافه می‌کنند و زمانی که مدیریت‌کننده رویداد به فعال‌شدن رویداد واکنش نشان داد، پیامی را ثبت می‌کنند.

با استفاده از `addEventListener()`:

```js
const video = document.querySelector("#video");
const button = document.querySelector("#button");

function onExitPip() {
  console.log("Picture-in-Picture mode deactivated!");
}

video.addEventListener("leavepictureinpicture", onExitPip);

button.onclick = () => {
  if (document.pictureInPictureElement) {
    document.exitPictureInPicture();
  }
};
```

با استفاده از ویژگی مدیریت‌کننده رویداد `onleavepictureinpicture`:

```js
const video = document.querySelector("#video");
const button = document.querySelector("#button");

function onExitPip() {
  console.log("Picture-in-Picture mode deactivated!");
}

video.onleavepictureinpicture = onExitPip;

button.onclick = () => {
  if (document.pictureInPictureElement) {
    document.exitPictureInPicture();
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLVideoElement")}}
- [Picture-in-Picture API](/en-US/docs/Web/API/Picture-in-Picture_API)