---
title: "MediaTrackSettings: aspectRatio property"
short-title: aspectRatio
slug: Web/API/MediaTrackSettings/aspectRatio
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.aspectRatio_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`aspectRatio`** از فرهنگ {{domxref("MediaTrackSettings")}} یک عدد اعشاری با دقت دوبرابر است که {{glossary("aspect ratio", "نسبت تصویر")}} فعلی {{domxref("MediaStreamTrack")}} را نشان می‌دهد.
این ویژگی به شما امکان می‌دهد تا مشخص کنید چه مقداری برای مطابقت با محدودیت‌های تعیین‌شده‌تان برای این ویژگی انتخاب شده است، همانطور که در ویژگی {{domxref("MediaTrackConstraints.aspectRatio")}} هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.aspectRatio")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، از پشتیبانی یا عدم پشتیبانی از این محدودیت مطلع شوید. با این حال، معمولاً این کار ضروری نیست زیرا مرورگرها هر محدودیتی را که ناآشنا باشند نادیده می‌گیرند.

## مقدار

یک عدد اعشاری با دقت دوبرابر که پیکربندی فعلی نسبت تصویر ردگیری (track) را نشان می‌دهد. نسبت تصویر با گرفتن عرض ردگیری، تقسیم بر ارتفاع آن و گرد کردن نتیجه به ده رقم اعشار محاسبه می‌شود. به عنوان مثال، نسبت تصویر استاندارد 16:9 با وضوح بالا را می‌توان به صورت 1920/1080 یا 1.7777777778 محاسبه کرد.

## مثال‌ها

به مثال [تمرین‌کننده محدودیت (Constraint exerciser)](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان‌های رسانه‌ای](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.aspectRatio")}}
- {{domxref("MediaTrackSettings")}}