---
title: "MediaTrackSettings: frameRate property"
short-title: frameRate
slug: Web/API/MediaTrackSettings/frameRate
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.frameRate_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`frameRate`** در دیکشنری {{domxref("MediaTrackSettings")}} یک عدد ممیز شناور با دقت مضاعف است که نرخ فریم {{domxref("MediaStreamTrack")}} را مطابق پیکربندی فعلی، بر حسب فریم در ثانیه، نشان می‌دهد. این ویژگی به شما امکان می‌دهد تعیین کنید که برای مطابقت با محدودیت‌هایی که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} از طریق ویژگی {{domxref("MediaTrackConstraints.frameRate")}} تعیین کرده بودید، چه مقداری برای این ویژگی انتخاب شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.frameRate")}} که با فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، متوجه شوید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که نمی‌شناسند نادیده می‌گیرند.

## مقدار

یک عدد ممیز شناور با دقت مضاعف است که پیکربندی فعلی نرخ فریمِ ترک (track) را بر حسب فریم در ثانیه نشان می‌دهد.

## نمونه‌ها

نمونهٔ [تمرینگر محدودیت](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.frameRate")}}
- {{domxref("MediaTrackSettings")}}