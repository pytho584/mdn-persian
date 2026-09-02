---
title: "MediaTrackConstraints: sampleRate property"
short-title: sampleRate
slug: Web/API/MediaTrackConstraints/sampleRate
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.sampleRate_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`sampleRate`** در فرهنگ لغت {{domxref("MediaTrackConstraints")}} یک [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) است که محدودیت‌های درخواستی یا اجباری را بر روی مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.sampleRate", "sampleRate")}} توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.sampleRate")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

اگر این مقدار یک عدد باشد، عامل کاربر (user agent) تلاش می‌کند رسانه‌ای را به دست آورد که نرخ نمونه‌برداری آن تا حد امکان به این عدد نزدیک باشد، با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده. در غیر این صورت، مقدار این [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) عامل کاربر را در تلاش برای ارائه تطابق دقیق با نرخ نمونه‌برداری موردنیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا مقدار بهترین ممکن راهنمایی می‌کند.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}