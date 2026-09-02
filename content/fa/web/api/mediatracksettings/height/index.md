---
title: "MediaTrackSettings: height property"
short-title: height
slug: Web/API/MediaTrackSettings/height
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.height_constraint
---

{{APIRef("Media Capture and Streams")}}

خاصیت **`height`** در فرهنگ لغت {{domxref("MediaTrackSettings")}} یک عدد صحیح است که نشان می‌دهد {{domxref("MediaStreamTrack")}} در حال حاضر برای چه تعداد پیکسل ارتفاع پیکربندی شده است. این امکان را به شما می‌دهد تا تعیین کنید چه مقداری برای برآوردن محدودیت‌های مشخص‌شدهٔ شما برای این خاصیت انتخاب شده است؛ همان‌طور که در خاصیت {{domxref("MediaTrackConstraints.height")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید، توضیح داده شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.height")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنایی نداشته باشند نادیده می‌گیرند.

## مقدار

یک عدد صحیح که ارتفاع ویدیو را بر حسب پیکسل، مطابق پیکربندی فعلی نشان می‌دهد.

## مثال‌ها

به مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.height")}}
- {{domxref("MediaTrackSettings")}}