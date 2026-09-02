---
title: "MediaTrackSettings: sampleRate property"
short-title: sampleRate
slug: Web/API/MediaTrackSettings/sampleRate
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.sampleRate_constraint
---

{{APIRef("Media Capture and Streams")}}

خاصیت **`sampleRate`** از فرهنگ {{domxref("MediaTrackSettings")}} یک عدد صحیح است که نشان می‌دهد {{domxref("MediaStreamTrack")}} در حال حاضر برای چند نمونه صوتی در هر ثانیه پیکربندی شده است. این به شما امکان می‌دهد تعیین کنید کدام مقدار برای مطابقت با محدودیت‌های مشخص‌شده شما برای این خاصیت انتخاب شده است، همانطور که در خاصیت {{domxref("MediaTrackConstraints.sampleRate")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید، توضیح داده شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.sampleRate")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

یک عدد صحیح که نشان می‌دهد هر ثانیه از داده‌های صوتی شامل چند نمونه است. مقادیر رایج عبارتند از ۴۴٬۱۰۰ (صدای استاندارد CD)، ۴۸٬۰۰۰ (صدای دیجیتال استاندارد)، ۹۶٬۰۰۰ (که معمولاً در مسترینگ و پس از تولید صدا استفاده می‌شود)، و ۱۹۲٬۰۰۰ (که برای صدای با وضوح بالا در ضبط و مسترینگ حرفه‌ای استفاده می‌شود). با این حال، مقادیر پایین‌تر اغلب برای کاهش نیازهای پهنای باند استفاده می‌شوند؛ ۸٬۰۰۰ نمونه در ثانیه برای گفتار قابل فهم هرچند ناقص انسان کافی است، و هر دو ۱۱٬۰۲۵ و ۲۲٬۰۵۰ نمونه در ثانیه اغلب برای صدا و موسیقی با پهنای باند کم و کیفیت کاهش‌یافته استفاده می‌شوند.

## مثال‌ها

به مثال [تمرین‌کننده محدودیت‌ها](/fa/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان‌های رسانه](/fa/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/fa/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.sampleRate")}}
- {{domxref("MediaTrackSettings")}}