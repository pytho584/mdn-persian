---
title: "MediaStreamTrack: muted property"
short-title: muted
slug: Web/API/MediaStreamTrack/muted
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.muted
---

{{APIRef("Media Capture and Streams")}}

ویژگی فقط‌خواندنی **`muted`** در رابط {{domxref("MediaStreamTrack")}} یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا این Track در حال حاضر قادر به ارائه خروجی رسانه نیست یا خیر.

> [!NOTE]
> برای پیاده‌سازی روشی که کاربران بتوانند یک Track را بی‌صدا یا با صدا کنند، از ویژگی {{domxref("MediaStreamTrack.enabled", "enabled")}} استفاده کنید. وقتی یک Track با قرار دادن `enabled` روی `false` غیرفعال می‌شود، فقط فریم‌های خالی تولید می‌کند (فریم‌های صوتی که هر نمونه آن ۰ است، یا فریم‌های ویدیویی که هر پیکسل آن سیاه است).

## مقدار

یک مقدار بولین که اگر Track در حال حاضر بی‌صدا باشد `true` است، و اگر Track در حال حاضر با صدا باشد `false` است.

> [!NOTE]
> در صورت امکان، از بررسی مکرر `muted` برای نظارت بر وضعیت بی‌صدا بودن Track خودداری کنید. در عوض، شنونده‌های رویداد را برای رویدادهای {{domxref("MediaStreamTrack.mute_event", "mute")}} و {{domxref("MediaStreamTrack.unmute_event", "unmute")}} اضافه کنید.

## مثال‌ها

این مثال تعداد Trackهایی را در یک آرایه از اشیاء {{domxref("MediaStreamTrack")}} که در حال حاضر بی‌صدا هستند، شمارش می‌کند.

```js
let mutedCount = 0;

trackList.forEach((track) => {
  if (track.muted) {
    mutedCount += 1;
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}