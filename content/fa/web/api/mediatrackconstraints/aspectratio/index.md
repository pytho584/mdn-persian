---
title: "MediaTrackConstraints: aspectRatio property"
---

---
title: "MediaTrackConstraints: aspectRatio property"
short-title: aspectRatio
slug: Web/API/MediaTrackConstraints/aspectRatio
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.aspectRatio_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`aspectRatio`** در دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی محدودیت‌پذیر {{domxref("MediaTrackSettings.aspectRatio", "aspectRatio")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.aspectRatio")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} برگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنایی ندارند نادیده می‌گیرند.

## مقدار

یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) که مقدار(های) قابل قبول یا الزامی را برای {{glossary("aspect ratio")}} یک تراک ویدیو توصیف می‌کند. این مقدار، حاصل تقسیم عرض بر ارتفاع است و تا ده رقم اعشار گرد می‌شود. برای مثال، نسبت تصویر استاندارد ویدیوی با کیفیت بالا (HD) یعنی 16:9 را می‌توان به صورت 1920/1080 یا 1.7777777778 محاسبه کرد.

اگر این مقدار یک عدد باشد، عامل کاربر (user agent) تلاش می‌کند رسانه‌ای به دست آورد که نسبت تصویر آن، با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده، تا حد امکان به این عدد نزدیک باشد. در غیر این صورت، مقدار این [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) عامل کاربر را در تلاش برای ارائه تطبیق دقیق با نسبت تصویر موردنیاز (در صورت مشخص شدن `exact` یا ارائه شدن هر دو `min` و `max` با مقدار یکسان) یا رسیدن به بهترین مقدار ممکن راهنمایی می‌کند.

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