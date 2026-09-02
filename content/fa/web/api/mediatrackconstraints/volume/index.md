---
title: "MediaTrackConstraints: volume property"
short-title: volume
slug: Web/API/MediaTrackConstraints/volume
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MediaStreamTrack.applyConstraints.volume_constraint
---

{{APIRef("Media Capture and Streams")}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی **`volume`** در دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی محدودپذیر {{domxref("MediaTrackSettings.volume", "volume")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.volume")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تشخیص دهید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست؛ زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) که مقدار(های) قابل‌قبول یا الزامی برای بلندی صدای یک تراک صوتی را توصیف می‌کند؛ بر روی یک مقیاس خطی که در آن 0.0 به معنای سکوت و 1.0 بالاترین بلندی صدای پشتیبانی‌شده است.

اگر این مقدار یک عدد باشد، عامل کاربر تلاش می‌کند رسانه‌ای را به‌دست آورد که بلندی صدای آن، با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده، تا حد امکان به این عدد نزدیک باشد. در غیر این صورت، مقدار این [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) عامل کاربر را در تلاش برای ایجاد تطابق دقیق با بلندی صدای موردنیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا برای رسیدن به بهترین مقدار ممکن هدایت می‌کند.

هر مجموعه محدودیتی که فقط مقادیر خارج از بازه 0.0 تا 1.0 را مجاز بداند، قابل برآورده شدن نیست و به شکست منجر می‌شود.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}