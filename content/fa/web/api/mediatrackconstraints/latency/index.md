---
title: "MediaTrackConstraints: latency property"
short-title: latency
slug: Web/API/MediaTrackConstraints/latency
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.latency_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`latency`** در فرهنگ واژه‌نامه {{domxref("MediaTrackConstraints")}}
یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) است
که محدودیت‌های درخواستی یا اجباری را بر روی مقدار ویژگی قابل‌قید
{{domxref("MediaTrackSettings.latency", "latency")}} توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار
{{domxref("MediaTrackSupportedConstraints.latency")}} که توسط فراخوانی
{{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

از آنجا که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، مسیرهای مرتبط با یک
{{domxref("RTCPeerConnection")}} در [WebRTC](/en-US/docs/Web/API/WebRTC_API)
هرگز این ویژگی را شامل نخواهند شد.

## مقدار

یک [`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble) که مقدار قابل قبول یا الزامی را برای تأخیر (latency) مسیر صوتی توصیف می‌کند؛ مقادیر بر حسب ثانیه مشخص می‌شوند. در پردازش صوتی، تأخیر (latency) زمان بین شروع پردازش (زمانی که صدا در دنیای واقعی رخ می‌دهد یا توسط یک دستگاه سخت‌افزاری تولید می‌شود) و در دسترس قرار گرفتن داده‌ها برای مرحله بعدی در فرآیند ورودی یا خروجی صوتی است. در بیشتر موارد، تأخیر کم برای عملکرد و تجربه کاربری مطلوب است، اما زمانی که مصرف انرژی اهمیت دارد یا تأخیرها به‌هرحال قابل قبول هستند، تأخیر بیشتر ممکن است قابل قبول باشد.

اگر مقدار این ویژگی یک عدد باشد، عامل کاربر (user agent) تلاش خواهد کرد رسانه‌ای به دست آورد که تأخیر آن با توجه به قابلیت‌های سخت‌افزار و سایر محدودیت‌های مشخص‌شده، تا حد امکان به این عدد نزدیک باشد. در غیر این صورت، مقدار این
[`ConstrainDouble`](/en-US/docs/Web/API/MediaTrackConstraints#constraindouble)
عامل کاربر را در تلاش برای ارائه تطابق دقیق با تأخیر مورد نیاز (اگر `exact` مشخص شده باشد یا هر دو `min` و `max` ارائه شده و مقدار یکسانی داشته باشند) یا با بهترین مقدار ممکن راهنمایی می‌کند.

> [!NOTE]
> تأخیر همیشه به دلیل نیازهای استفاده از سخت‌افزار، محدودیت‌های شبکه و غیره در معرض تغییراتی است؛ بنابراین حتی در حالت تطابق «دقیق» نیز باید انتظار تغییرات جزئی را داشت.

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