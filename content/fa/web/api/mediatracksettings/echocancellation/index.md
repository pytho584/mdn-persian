```
---
title: "MediaTrackSettings: echoCancellation property"
short-title: echoCancellation
slug: Web/API/MediaTrackSettings/echoCancellation
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.echoCancellation_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`echoCancellation`** از {{domxref("MediaTrackSettings")}} یک مقدار بولی است که نشان می‌دهد آیا قابلیت حذف پژواک (echo cancellation) روی یک مسیر صوتی فعال است یا نه. این به شما امکان می‌دهد تعیین کنید برای رعایت محدودیت‌هایی که برای مقدار این ویژگی تعیین کرده بودید، چه مقداری انتخاب شده است؛ همان‌طور که در ویژگی {{domxref("MediaTrackConstraints.echoCancellation")}} توصیف شده است، همان محدودیتی که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید.

حذف پژواک قابلیتی است که با کاهش یا حذف تداخل (crosstalk) بین دستگاه خروجی و دستگاه ورودی کاربر، تلاش می‌کند از ایجاد افکت پژواک در اتصال صوتی دوطرفه جلوگیری کند. برای مثال، ممکن است فیلتری اعمال کند که صدای تولیدشده توسط بلندگوها را از مسیر ورودیِ حاصل از میکروفون حذف کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.echoCancellation")}} که در نتیجهٔ فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا نه. با این حال، معمولاً این کار ضروری نیست؛ زیرا مرورگرها هر محدودیتی را که با آن آشنا نیستند نادیده می‌گیرند.

ازآنجاکه {{Glossary("RTP")}} این اطلاعات را در بر ندارد، مسیرهای مرتبط با یک {{domxref("RTCPeerConnection")}} در [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز شامل این ویژگی نخواهند بود.

## مقدار

یک مقدار بولی که اگر قابلیت حذف پژواک در مسیر فعال شده باشد، `true` و اگر حذف پژواک غیرفعال باشد، `false` است.

## مثال‌ها

مثال [تمرین‌دهندهٔ محدودیت‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.echoCancellation")}}
- {{domxref("MediaTrackSettings")}}
```