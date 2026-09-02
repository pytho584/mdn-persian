---
title: "MediaTrackConstraints: sampleSize property"
---

---
title: "MediaTrackConstraints: sampleSize property"
short-title: sampleSize
slug: Web/API/MediaTrackConstraints/sampleSize
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.sampleSize_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`sampleSize`** از دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودسازی {{domxref("MediaTrackSettings.sampleSize", "sampleSize")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.sampleSize")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنایی نداشته باشند نادیده می‌گیرند.

## مقدار

اگر این مقدار یک عدد باشد، عامل کاربر (user agent) تلاش می‌کند رسانه‌ای را به دست آورد که اندازه نمونه آن (بر حسب بیت به ازای هر نمونه خطی) با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده، تا حد ممکن به این عدد نزدیک باشد. در غیر این صورت، مقدار این [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) عامل کاربر را در تلاش برای ارائه تطابق دقیق با اندازه نمونه مورد نیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا رسیدن به بهترین مقدار ممکن هدایت می‌کند.

> [!NOTE]
> از آنجا که این ویژگی فقط می‌تواند اندازه‌های نمونه خطی را نشان دهد، این محدودیت تنها توسط دستگاه‌هایی قابل برآورده شدن است که می‌توانند صدایی با نمونه‌های خطی تولید کنند.

## مثال‌ها

نمونه [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}