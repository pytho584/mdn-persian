---
title: "MediaTrackConstraints: channelCount property"
---

---
title: "MediaTrackConstraints: channelCount property"
short-title: channelCount
slug: Web/API/MediaTrackConstraints/channelCount
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.channelCount_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`channelCount`** در فرهنگ {{domxref("MediaTrackConstraints")}} یک [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) است که محدودیت‌های درخواستی یا الزامی اعمال‌شده بر مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.channelCount", "channelCount")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.channelCount")}} که از طریق فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

اگر این مقدار یک عدد باشد، عامل کاربر (user agent) تلاش می‌کند رسانه‌ای به دست آورد که تعداد کانال‌های آن تا حد امکان به این عدد نزدیک باشد، با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده. در غیر این صورت، مقدار این [`ConstrainULong`](/en-US/docs/Web/API/MediaTrackConstraints#constrainulong) عامل کاربر را در تلاش‌هایش برای ارائه یک تطابق دقیق با تعداد کانال مورد نیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا یک مقدار تا حد امکان بهینه راهنمایی می‌کند.

تعداد کانال‌ها برای صدای مونورال (تک‌کاناله) ۱، برای صدای استریو ۲، و به همین ترتیب است.

## مثال‌ها

به مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}