---
title: "MediaDevices: enumerateDevices() method"
short-title: enumerateDevices()
slug: Web/API/MediaDevices/enumerateDevices
page-type: web-api-instance-method
browser-compat: api.MediaDevices.enumerateDevices
---

{{APIRef("Media Capture and Streams")}}{{SecureContext_Header}}

متد **`enumerateDevices()`** از رابط {{domxref("MediaDevices")}} فهرستی از دستگاه‌های ورودی و خروجی رسانه‌ایِ در دسترس، مانند میکروفون‌ها، دوربین‌ها، هدست‌ها و غیره را درخواست می‌کند. {{jsxref("Promise")}} برگشتی با آرایه‌ای از اشیاء {{domxref("MediaDeviceInfo")}} که دستگاه‌ها را توصیف می‌کنند، حل می‌شود.

فهرست برگشتی هر دستگاهی را که توسط [سیاست مجوز (Permission Policy)](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy) سند مسدود شده است، حذف می‌کند: [`microphone`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/microphone)، [`camera`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/camera)، [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) (برای دستگاه‌های خروجی)، و غیره. دسترسی به دستگاه‌های غیرپیش‌فرض خاص نیز توسط [API مجوزها (Permissions API)](/en-US/docs/Web/API/Permissions_API) کنترل می‌شود و فهرست، دستگاه‌هایی را که کاربر مجوز صریح به آن‌ها نداده است حذف می‌کند.

## سینتکس

```js-nolint
enumerateDevices()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از اشیاء {{domxref("MediaDeviceInfo")}} محقق می‌شود. هر شیء در آرایه یکی از دستگاه‌های ورودی و خروجی رسانه‌ای موجود را توصیف می‌کند. ترتیب اهمیت دارد — دستگاه‌های ضبط پیش‌فرض ابتدا فهرست می‌شوند.

به جز دستگاه‌های پیش‌فرض، تنها دستگاه‌هایی که برایشان مجوز صادر شده است «در دسترس» هستند.

اگر دستگاه رسانه‌ای یک دستگاه ورودی باشد، به جای آن یک شیء {{domxref("InputDeviceInfo")}} برگردانده می‌شود.

اگر شمارش (enumeration) با شکست مواجه شود، promise رد می‌شود.

## الزامات امنیتی

دسترسی به API منوط به محدودیت‌های زیر است:

- متد باید در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) فراخوانی شود.
- سند باید کاملاً فعال باشد و وضعیت نمایان بودن آن «نمایان» (visible) باشد.

## نمونه‌ها

در اینجا نمونه‌ای از استفاده از `enumerateDevices()` آورده شده است. این نمونه فهرستی از [شناسه‌های دستگاه](/en-US/docs/Web/API/MediaDeviceInfo/deviceId) را همراه با برچسب‌های آن‌ها (در صورت وجود) چاپ می‌کند.

```js
if (!navigator.mediaDevices?.enumerateDevices) {
  console.log("enumerateDevices() not supported.");
} else {
  // List cameras and microphones.
  navigator.mediaDevices
    .enumerateDevices()
    .then((devices) => {
      devices.forEach((device) => {
        console.log(`${device.kind}: ${device.label} id = ${device.deviceId}`);
      });
    })
    .catch((err) => {
      console.error(`${err.name}: ${err.message}`);
    });
}
```

این ممکن است خروجی زیر را تولید کند:

```plain
videoinput: id = csO9c0YpAf274OuCPUA53CNE0YHlIr2yXCi+SqfBZZ8=
audioinput: id = RKxXByjnabbADGQNNZqLVLdmXlS0YkETYCIbg+XxnvM=
audioinput: id = r2/xw1xUPIyZunfV1lGrKOma5wTOvCkWfZ368XCndm0=
```

یا اگر یک یا چند {{domxref("MediaStream")}} فعال باشند یا مجوزهای ماندگار صادر شده باشند:

```plain
videoinput: FaceTime HD Camera (Built-in) id=csO9c0YpAf274OuCPUA53CNE0YHlIr2yXCi+SqfBZZ8=
audioinput: default (Built-in Microphone) id=RKxXByjnabbADGQNNZqLVLdmXlS0YkETYCIbg+XxnvM=
audioinput: Built-in Microphone id=r2/xw1xUPIyZunfV1lGrKOma5wTOvCkWfZ368XCndm0=
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaDevices.getUserMedia")}}
- [WebRTC](/en-US/docs/Web/API/WebRTC_API) — صفحه معرفی API
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API) — API برای اشیاء جریان رسانه‌ای
- [گرفتن عکس با وب‌کم](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Taking_still_photos) — یک آموزش درباره استفاده از `getUserMedia()` برای گرفتن عکس به جای ویدیو.