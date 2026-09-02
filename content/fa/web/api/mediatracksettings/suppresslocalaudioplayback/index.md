---
title: "MediaTrackSettings: suppressLocalAudioPlayback property"
short-title: suppressLocalAudioPlayback
slug: Web/API/MediaTrackSettings/suppressLocalAudioPlayback
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.applyConstraints.suppressLocalAudioPlayback_constraint
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

ویژگی **`suppressLocalAudioPlayback`** در دیکشنری {{domxref("MediaTrackSettings")}} کنترل می‌کند که آیا صدای در حال پخش در یک تب، هنگام ضبط آن تب، همچنان از بلندگوهای محلی کاربر پخش شود یا نه.

به‌عنوان مثال، در مواردی که تماس ویدیویی را به یک سیستم صوتی-تصویری خارجی در اتاق کنفرانس پخش می‌کنید، می‌خواهید صدا از سیستم صوتی-تصویری خارج شود، نه از بلندگوهای محلی. به این ترتیب، صدا بلندتر و واضح‌تر خواهد بود و همچنین با ویدیوی کنفرانس هماهنگ خواهد بود.

## Value

مقدار `suppressLocalAudioPlayback` یک بولی است — `true` سرکوب پخش صوتی محلی را فعال می‌کند و `false` آن را غیرفعال می‌کند.

## Examples

تابع زیر یک شیء محدودیت‌ها (constraints) را تنظیم می‌کند که گزینه‌های فراخوانی {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} را مشخص می‌کند. این تابع محدودیت `suppressLocalAudioPlayback` را (با درخواست اینکه صدای ضبط‌شده از بلندگوهای محلی کاربر پخش نشود) فقط در صورتی اضافه می‌کند که مشخص باشد توسط مرورگر پشتیبانی می‌شود. سپس ضبط با فراخوانی `getDisplayMedia()` شروع می‌شود و استریم بازگشتی به عنصر ویدیویی که توسط متغیر `videoElem` ارجاع داده شده است، متصل می‌شود.

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the screen capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}