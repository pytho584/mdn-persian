---
title: "MediaTrackConstraints: width property"
short-title: width
slug: Web/API/MediaTrackConstraints/width
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.width_constraint
---

{{APIRef("Media Capture and Streams")}}

خصوصیت **`width`** در فرهنگ لغت {{domxref("MediaTrackConstraints")}} یک [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.width", "width")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.width")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} به دست می‌آید، تشخیص دهید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

اگر این مقدار یک عدد باشد، عامل کاربر تلاش می‌کند رسانه‌ای با عرضی تا حد امکان نزدیک به این عدد، با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده، به دست آورد. در غیر این صورت، مقدار این [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) عامل کاربر را در تلاش برای ارائه تطابق دقیق با عرض موردنیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا رسیدن به بهترین مقدار ممکن راهنمایی می‌کند.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}