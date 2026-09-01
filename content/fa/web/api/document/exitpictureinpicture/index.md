---
title: "Document: exitPictureInPicture() method"
short-title: exitPictureInPicture()
slug: Web/API/Document/exitPictureInPicture
page-type: web-api-instance-method
browser-compat: api.Document.exitPictureInPicture
---

{{APIRef("Picture-in-Picture API")}}

متد **`exitPictureInPicture()`** از رابط {{domxref("Document")}} درخواست می‌دهد که یک ویدئوی موجود در این سند که در حال حاضر به صورت شناور (Picture-in-Picture) قرار دارد، از حالت تصویر در تصویر خارج شود و حالت قبلی صفحه بازگردانده شود. این معمولاً اثر فراخوانی قبلی {{domxref("HTMLVideoElement.requestPictureInPicture()")}} را معکوس می‌کند.

## Syntax

```js-nolint
exitPictureInPicture()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به محض پایان یافتن خروج {{Glossary("user agent")}} از حالت تصویر در تصویر (Picture-in-Picture) حل می‌شود. اگر در هنگام تلاش برای خروج از حالت تمام صفحه خطایی رخ دهد، کنترل‌کننده `catch()` پرامیس فراخوانی می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که `document.pictureInPictureElement` برابر با `null` باشد، پرتاب می‌شود.

## مثال‌ها

این مثال باعث می‌شود که سند جاری هر زمان که دکمه ماوس درون آن کلیک شود، از حالت تصویر در تصویر (Picture-in-Picture) خارج شود.

```js
document.onclick = (event) => {
  if (document.pictureInPictureElement) {
    document
      .exitPictureInPicture()
      .then(() => console.log("Document Exited from Picture-in-Picture mode"))
      .catch((err) => console.error(err));
  } else {
    video.requestPictureInPicture();
  }
};
```

توجه داشته باشید که اگر می‌خواهید پیگیری کنید کدام ویدئو در صفحه شما در حال حاضر در حالت تصویر در تصویر (Picture-in-Picture) در حال پخش است، باید به رویدادهای `enterpictureinpicture` و `leavepictureinpicture` روی عنصر(های) {{DOMxRef("HTMLVideoElement")}} مورد نظر گوش دهید. به‌طور جایگزین، می‌توانید بررسی کنید که آیا {{DOMxRef("Document.pictureInPictureElement")}} به عنصر {{DOMxRef("HTMLVideoElement")}} جاری اشاره می‌کند یا خیر.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}}
- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
- {{DOMxRef("Document.pictureInPictureEnabled")}}
- {{DOMxRef("Document.pictureInPictureElement")}}
- {{CSSxRef(":picture-in-picture")}}
- [رویدادهای Picture-in-Picture](/en-US/docs/Web/API/Picture-in-Picture_API#events)