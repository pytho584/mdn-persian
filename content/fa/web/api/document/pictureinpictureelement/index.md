```
---
title: "Document: pictureInPictureElement property"
short-title: pictureInPictureElement
slug: Web/API/Document/pictureInPictureElement
page-type: web-api-instance-property
browser-compat: api.Document.pictureInPictureElement
---

{{APIRef("Picture-in-Picture API")}}

ویژگی فقط‑خواندنی **`pictureInPictureElement`** از رابط {{domxref("Document")}}، عنصر {{domxref("Element")}}ای را برمی‌گرداند که در حال حاضر در این سند در حالت تصویر در تصویر (picture-in-picture) نمایش داده می‌شود، یا اگر حالت تصویر در تصویر فعال نباشد `null` را برمی‌گرداند.

اگرچه این ویژگی فقط‑خواندنی است، اما در صورت تغییر (حتی در حالت strict) خطا پرتاب نمی‌کند؛ setter آن یک عملیات بی‌اثر است و نادیده گرفته می‌شود.

## مقدار

یک ارجاع به شیء {{domxref("Element")}} که در حال حاضر در حالت تصویر در تصویر است.

اگر سند هیچ عنصر مرتبطی در حالت تصویر در تصویر نداشته باشد `null` را برمی‌گرداند. برای مثال، هیچ عنصر تصویر در تصویری وجود ندارد، یا عنصر از یک iframe است.

## مثال‌ها

این مثال یک تابع به نام `exitPictureInPicture()` را ارائه می‌دهد که مقدار بازگشتی از `pictureInPictureElement` را بررسی می‌کند. اگر سند در حالت تصویر در تصویر باشد (`pictureInPictureElement` برابر `null` نباشد)، [`Document.exitPictureInPicture()`](/en-US/docs/Web/API/Document/exitPictureInPicture) برای خروج از حالت تصویر در تصویر اجرا می‌شود.

```js
function exitPictureInPicture() {
  if (document.pictureInPictureElement) {
    document.exitPictureInPicture();
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}}
- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
- {{DOMxRef("Document.pictureInPictureEnabled")}}
- {{DOMxRef("Document.exitPictureInPicture()")}}
- {{CSSxRef(":picture-in-picture")}}
```