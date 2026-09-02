```
---
title: "MediaTrackSettings: autoGainControl property"
short-title: autoGainControl
slug: Web/API/MediaTrackSettings/autoGainControl
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.autoGainControl_constraint
---

{{APIRef("Media Capture and Streams")}}

دیکشنری {{domxref("MediaTrackSettings")}} دارای ویژگی **`autoGainControl`** است که یک مقدار بولی است و نشان می‌دهد که آیا کنترل خودکار بهره (AGC) روی یک تراک صوتی فعال شده است یا خیر. این ویژگی به شما امکان می‌دهد مشخص کنید کدام مقدار برای رعایت محدودیت‌های مشخص‌شده‌تان برای این ویژگی انتخاب شده است، همانطور که در ویژگی {{domxref("MediaTrackConstraints.autoGainControl")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید، توضیح داده شده است.

کنترل خودکار بهره قابلیتی است که در آن یک منبع صوتی به‌طور خودکار تغییرات حجم رسانه مبدأ خود را مدیریت می‌کند تا سطح کلی حجم ثابتی حفظ شود. این قابلیت معمولاً روی میکروفون‌ها استفاده می‌شود، اما می‌تواند توسط سایر منابع ورودی نیز ارائه شود.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.autoGainControl")}} که توسط یک فراخوانی به {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن‌ها آشنا نیستند نادیده می‌گیرند.

## مقدار

یک مقدار بولی که اگر تراک دارای کنترل خودکار بهره فعال باشد `true` است و اگر AGC غیرفعال باشد `false` است.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.autoGainControl")}}
- {{domxref("MediaTrackSupportedConstraints")}}
```