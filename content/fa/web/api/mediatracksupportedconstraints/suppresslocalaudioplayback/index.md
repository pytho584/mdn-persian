---
title: "MediaTrackSupportedConstraints: suppressLocalAudioPlayback property"
---

---
title: "MediaTrackSupportedConstraints: suppressLocalAudioPlayback property"
short-title: suppressLocalAudioPlayback
slug: Web/API/MediaTrackSupportedConstraints/suppressLocalAudioPlayback
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.applyConstraints.suppressLocalAudioPlayback_constraint
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

ویژگی **`suppressLocalAudioPlayback`** از دیکشنری {{domxref("MediaTrackSupportedConstraints")}} مشخص می‌کند که آیا محدودیت {{domxref("MediaTrackConstraints.suppressLocalAudioPlayback", "suppressLocalAudioPlayback")}} توسط عامل کاربر و دستگاهی که محتوا روی آن استفاده می‌شود پشتیبانی می‌شود یا خیر.

لیست محدودیت‌های پشتیبانی‌شده با فراخوانی {{domxref("MediaDevices.getSupportedConstraints","navigator.mediaDevices.getSupportedConstraints()")}} به دست می‌آید.

## مقدار

یک مقدار بولی که `true` است اگر محدودیت {{domxref("MediaTrackConstraints.suppressLocalAudioPlayback", "suppressLocalAudioPlayback")}} توسط دستگاه و عامل کاربر پشتیبانی شود.

## مثال‌ها

تابع زیر یک شیء گزینه‌ها را برای فراخوانی {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} تنظیم می‌کند. این تابع محدودیت `suppressLocalAudioPlayback` را (که درخواست می‌کند صدای ضبط‌شده از بلندگوهای محلی کاربر پخش نشود) تنها در صورتی اضافه می‌کند که مشخص باشد توسط مرورگر پشتیبانی می‌شود. سپس ضبط با فراخوانی `getDisplayMedia()` و متصل کردن جریان برگشتی به عنصر ویدیویی که توسط متغیر `videoElem` ارجاع داده شده است، شروع می‌شود.

```js
async function capture() {
  const supportedConstraints = navigator.mediaDevices.getSupportedConstraints();
  const displayMediaOptions = {
    audio: {},
  };

  if (supportedConstraints.suppressLocalAudioPlayback) {
    displayMediaOptions.audio.suppressLocalAudioPlayback = true;
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

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the screen capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}