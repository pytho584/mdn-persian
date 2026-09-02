---
title: "MediaTrackConstraints: frameRate property"
short-title: frameRate
slug: Web/API/MediaTrackConstraints/frameRate
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.frameRate_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`frameRate`** در فرهنگ لغت {{domxref("MediaTrackConstraints")}} یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.frameRate", "frameRate")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.frameRate")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تشخیص دهید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنایی ندارند نادیده می‌گیرند.

## مقدار

یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) که مقدار(های) قابل‌قبول یا الزامی برای نرخ فریم یک ویدیو را بر حسب فریم در ثانیه توصیف می‌کند.

اگر این مقدار یک عدد باشد، عامل کاربر (user agent) تلاش خواهد کرد رسانه‌ای به دست آورد که نرخ فریم آن تا حد امکان به این عدد نزدیک باشد، با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده. در غیر این صورت، مقدار این [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) عامل کاربر را در تلاش برای ارائه تطابق دقیق با نرخ فریم موردنیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا در ارائه بهترین مقدار ممکن راهنمایی خواهد کرد.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}