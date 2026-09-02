---
title: "MediaTrackSettings: latency property"
short-title: latency
slug: Web/API/MediaTrackSettings/latency
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.latency_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`latency`** در فرهنگ لغت {{domxref("MediaTrackSettings")}} یک عدد اعشاری با دقت دوبرابر است که تأخیر تخمینی (به ثانیه) مربوط به {{domxref("MediaStreamTrack")}} را در پیکربندی فعلی نشان می‌دهد. این ویژگی به شما امکان می‌دهد تعیین کنید که برای مطابقت با محدودیت‌های مشخص‌شده شما برای این ویژگی، چه مقداری انتخاب شده است؛ همان‌طور که در ویژگی {{domxref("MediaTrackConstraints.latency")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید، توضیح داده شده است.

البته این مقدار یک تقریب است، زیرا تأخیر می‌تواند به دلایل مختلفی از جمله هزینه‌های پردازشی CPU، انتقال و ذخیره‌سازی تغییر کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.latency")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} به دست می‌آید، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنایی ندارند نادیده می‌گیرند.

از آنجایی که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، مسیرهای مرتبط با یک {{domxref("RTCPeerConnection")}} در [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز این ویژگی را شامل نخواهند شد.

## مقدار

یک عدد اعشاری با دقت دوبرابر که تأخیر تخمینی (به ثانیه) مسیر صوتی را در پیکربندی فعلی نشان می‌دهد.

## مثال‌ها

به مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API دریافت رسانه و جریان‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.latency")}}
- {{domxref("MediaTrackSettings")}}