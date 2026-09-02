---
title: "MediaTrackSupportedConstraints: displaySurface property"
short-title: displaySurface
slug: Web/API/MediaTrackSupportedConstraints/displaySurface
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.displaySurface_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`displaySurface`** در فرهنگ لغت {{domxref("MediaTrackSupportedConstraints")}} نشان می‌دهد که آیا محدودیت {{domxref("MediaTrackConstraints.displaySurface", "displaySurface")}} توسط عامل کاربر (user agent) و دستگاهی که محتوا روی آن استفاده می‌شود پشتیبانی می‌شود یا خیر.

فهرست محدودیت‌های پشتیبانی‌شده با فراخوانی {{domxref("MediaDevices.getSupportedConstraints","navigator.mediaDevices.getSupportedConstraints()")}} به دست می‌آید.

## مقدار

یک مقدار بولی که اگر محدودیت {{domxref("MediaTrackConstraints.displaySurface", "displaySurface")}} توسط دستگاه و عامل کاربر پشتیبانی شود، `true` است.

## مثال‌ها

این متد، شیء محدودیت‌ها را با مشخص کردن گزینه‌های فراخوانی {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} تنظیم می‌کند. محدودیت `displaySurface` (با درخواست اجازه‌دهی فقط به اشتراک‌گذاری تمام‌صفحه) فقط در صورتی اضافه می‌شود که مشخص باشد مرورگر از آن پشتیبانی می‌کند. سپس ضبط با فراخوانی `getDisplayMedia()` و اتصال جریان برگشتی به عنصر ویدیویی که توسط متغیر `videoElem` ارجاع داده شده است، آغاز می‌شود.

```js
async function capture() {
  let supportedConstraints = navigator.mediaDevices.getSupportedConstraints();
  let displayMediaOptions = {
    video: {},
    audio: false,
  };

  if (supportedConstraints.displaySurface) {
    displayMediaOptions.video.displaySurface = "monitor";
  }

  try {
    videoElem.srcObject =
      await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
  } catch (err) {
    /* handle the error */
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the screen capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}