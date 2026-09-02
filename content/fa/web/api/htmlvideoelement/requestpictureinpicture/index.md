---
title: "HTMLVideoElement: requestPictureInPicture() method"
---

---
title: "HTMLVideoElement: requestPictureInPicture() method"
short-title: requestPictureInPicture()
slug: Web/API/HTMLVideoElement/requestPictureInPicture
page-type: web-api-instance-method
browser-compat: api.HTMLVideoElement.requestPictureInPicture
---

{{APIRef("Picture-in-Picture API")}}

متد **`requestPictureInPicture()`** در **{{domxref("HTMLVideoElement")}}** یک درخواست ناهمزمان برای نمایش ویدیو در حالت تصویر-در-تصویر (Picture-in-Picture) ارسال می‌کند.

تضمینی وجود ندارد که ویدیو وارد حالت تصویر-در-تصویر شود. اگر اجازه ورود به این حالت داده شود، {{jsxref("Promise")}} بازگشتی resolve می‌شود و ویدیو یک رویداد {{domxref("HTMLVideoElement.enterpictureinpicture_event", "enterpictureinpicture")}} دریافت می‌کند تا بداند که اکنون در حالت تصویر-در-تصویر قرار دارد.

## سینتکس

```js-nolint
requestPictureInPicture()
```

### پارامترها

هیچ پارامتری ندارد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء {{domxref("PictureInPictureWindow")}} resolve می‌شود و می‌توان از آن برای گوش دادن به رویداد تغییر اندازه (resize) پنجره شناور توسط کاربر استفاده کرد.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر این قابلیت پشتیبانی نشود (مثلاً توسط ترجیحات کاربر یا محدودیت پلتفرم غیرفعال شده باشد) پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر این قابلیت توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده باشد پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `readState` عنصر ویدیو برابر `HAVE_NOTHING` باشد، یا عنصر ویدیو هیچ track ویدیویی نداشته باشد، یا ویژگی `disablePictureInPicture` عنصر ویدیو برابر `true` باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر `document.pictureInPictureElement` برابر `null` باشد و سند دارای {{Glossary("transient activation")}} (فعال‌سازی گذرا) نباشد پرتاب می‌شود.

## امنیت

[Transient user activation](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این قابلیت کار کند.

## مثال‌ها

این مثال درخواست ورود ویدیو به حالت Picture-in-Picture را ارسال می‌کند و یک شنونده رویداد (event listener) برای مدیریت تغییر اندازه پنجره شناور تنظیم می‌کند.

```js
function enterPictureInPicture() {
  videoElement.requestPictureInPicture().then((pictureInPictureWindow) => {
    pictureInPictureWindow.addEventListener("resize", () =>
      onPipWindowResize(),
    );
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("video")}}
- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
- {{DOMxRef("Document.pictureInPictureEnabled")}}
- {{DOMxRef("Document.exitPictureInPicture()")}}
- {{DOMxRef("Document.pictureInPictureElement")}}
- {{CSSxRef(":picture-in-picture")}}