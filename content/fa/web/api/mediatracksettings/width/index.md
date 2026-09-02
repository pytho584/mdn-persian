---
title: "MediaTrackSettings: width property"
short-title: width
slug: Web/API/MediaTrackSettings/width
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.width_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`width`** در فرهنگ {{domxref("MediaTrackSettings")}} یک عدد صحیح است که نشان‌دهندهٔ تعداد پیکسل‌های عرضی است که {{domxref("MediaStreamTrack")}} در حال حاضر روی آن تنظیم شده است. این ویژگی به شما امکان می‌دهد تعیین کنید چه مقداری برای مطابقت با محدودیت‌های مشخص‌شده‌تان برای این ویژگی انتخاب شده است، همان‌طور که در ویژگی {{domxref("MediaTrackConstraints.width")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید، توضیح داده شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.width")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

یک مقدار عدد صحیح که عرض (بر حسب پیکسل) ردیف ویدیو را در حالت پیکربندی فعلی نشان می‌دهد.

## مثال‌ها

مثال [تمرین محدودیت‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.width")}}
- {{domxref("MediaTrackSettings")}}