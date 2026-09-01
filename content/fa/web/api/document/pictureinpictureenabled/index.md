---
title: "Document: pictureInPictureEnabled property"
---

{{APIRef("Picture-in-Picture API")}}

خاصیت فقط‌خواندنی **`pictureInPictureEnabled`** از رابط {{domxref("Document")}} مشخص می‌کند که آیا حالت تصویر-در-تصویر (Picture-in-Picture) در دسترس است یا نه.

حالت تصویر-در-تصویر به‌طور پیش‌فرض در دسترس است، مگر اینکه توسط [Permissions-Policy](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/picture-in-picture) به‌گونه‌ای دیگر تعیین شده باشد.

اگرچه این خاصیت فقط‌خواندنی است، تغییر دادن آن هیچ خطایی ایجاد نمی‌کند (حتی در حالت سخت‌گیرانه)؛ تنظیم‌کننده (setter) آن هیچ عملی انجام نمی‌دهد و نادیده گرفته می‌شود.

## مقدار

یک مقدار بولین که اگر ویدیو بتواند با فراخوانی {{domxref("HTMLVideoElement.requestPictureInPicture()")}} وارد حالت تصویر-در-تصویر شده و در یک پنجره شناور نمایش داده شود، `true` است. اگر حالت تصویر-در-تصویر در دسترس نباشد، این مقدار `false` است.

## مثال‌ها

در این مثال، قبل از تلاش برای وارد شدن به حالت تصویر-در-تصویر برای یک عنصر {{htmlElement("video")}}، مقدار `pictureInPictureEnabled` بررسی می‌شود تا اگر این قابلیت در دسترس نبود، فراخوانی انجام نشود.

```js
function requestPictureInPicture() {
  if (document.pictureInPictureEnabled) {
    videoElement.requestPictureInPicture();
  } else {
    console.log("Your browser cannot use picture-in-picture right now");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}}
- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
- {{DOMxRef("Document.exitPictureInPicture()")}}
- {{DOMxRef("Document.pictureInPictureElement")}}
- {{CSSxRef(":picture-in-picture")}}