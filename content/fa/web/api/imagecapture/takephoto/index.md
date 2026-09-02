---
title: "ImageCapture: takePhoto() method"
---

---
title: "ImageCapture: takePhoto() method"
short-title: takePhoto()
slug: Web/API/ImageCapture/takePhoto
page-type: web-api-instance-method
browser-compat: api.ImageCapture.takePhoto
---

{{APIRef("Image Capture API")}}

متد **`takePhoto()`** از رابط {{domxref("ImageCapture")}} یک نوردهی واحد را با استفاده از دستگاه ضبط ویدیویی که یک {{domxref("MediaStreamTrack")}} را تأمین می‌کند، می‌گیرد و یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{domxref("Blob")}} حاوی داده‌ها resolve می‌شود.

## سینتکس

```js-nolint
takePhoto()
takePhoto(photoSettings)
```

### پارامترها

- `photoSettings` {{optional_inline}}
  - : یک شیء که گزینه‌های عکس گرفته‌شده را تنظیم می‌کند. گزینه‌های موجود عبارت‌اند از:
    - `fillLightMode`
      - : تنظیم فلش دستگاه ضبط؛ یکی از `"auto"`، `"off"` یا `"flash"`.
    - `imageHeight`
      - : ارتفاع مطلوب تصویر به‌صورت یک عدد صحیح. اگر عامل کاربر (user agent) فقط ارتفاع‌های گسسته را پشتیبانی کند، نزدیک‌ترین مقدار ارتفاع به این تنظیم را انتخاب می‌کند.
    - `imageWidth`
      - : عرض مطلوب تصویر به‌صورت یک عدد صحیح. اگر عامل کاربر فقط عرض‌های گسسته را پشتیبانی کند، نزدیک‌ترین مقدار عرض به این تنظیم را انتخاب می‌کند.
    - `redEyeReduction`
      - : یک مقدار بولی که نشان می‌دهد در صورت موجود بودن، کاهش قرمزی چشم (red-eye reduction) استفاده شود یا نه.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{domxref("Blob")}} resolve می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر ویژگی `readyState` متعلق به `MediaStreamTrack` که به سازنده (constructor) داده شده است، `live` نباشد، پرتاب می‌شود.
- `UnknownError` {{domxref("DOMException")}}
  - : اگر عملیات به هر دلیلی نتواند کامل شود، پرتاب می‌شود.

## مثال‌ها

این مثال از این [نمونهٔ Simple Image Capture](https://simpl.info/imagecapture/) استخراج شده است. نشان می‌دهد که چگونه از {{jsxref("Promise")}} بازگشتی توسط `takePhoto()` برای کپی کردن {{domxref("Blob")}} برگشتی در یک عنصر {{htmlelement("img")}} استفاده کنیم. برای سادگی، نحوهٔ نمونه‌سازی (instantiate) شیء {{domxref("ImageCapture")}} را نشان نمی‌دهد.

```js
let takePhotoButton = document.querySelector("button#takePhoto");
let canvas = document.querySelector("canvas");

takePhotoButton.onclick = takePhoto;

function takePhoto() {
  imageCapture
    .takePhoto()
    .then((blob) => {
      console.log("Took photo:", blob);
      img.classList.remove("hidden");
      img.src = URL.createObjectURL(blob);
    })
    .catch((error) => {
      console.error("takePhoto() error: ", error);
    });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}