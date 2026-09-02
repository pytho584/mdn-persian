---
title: "MediaTrackSettings: facingMode property"
short-title: facingMode
slug: Web/API/MediaTrackSettings/facingMode
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.facingMode_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`facingMode`** در دیکشنری {{domxref("MediaTrackSettings")}} یک رشته است که جهتی را نشان می‌دهد که دوربین تولیدکنندهٔ ویدیوی موجود در {{domacro("MediaStreamTrack")}} در حال حاضر به سمت آن روبروست. این ویژگی به شما امکان می‌دهد تعیین کنید که برای رعایت محدودیت‌های مشخص‌شده‌تان، چه مقداری انتخاب شده است؛ همان‌طور که در ویژگی {{domxref("MediaTrackConstraints.facingMode")}} (که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} ارائه کرده‌اید) توضیح داده شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.facingMode")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} برمی‌گردد، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که نشناسند نادیده می‌گیرند.

از آنجا که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، مسیرهای (track) مرتبط با یک {{domxref("RTCPeerConnection")}} در [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز این ویژگی را شامل نخواهند شد.

## مقدار

رشته‌ای که مقدار آن یکی از رشته‌های موجود در [`VideoFacingModeEnum`](#videofacingmodeenum) است.

### VideoFacingModeEnum

رشته‌های زیر مقادیر مجاز برای حالت روبرو (facing mode) هستند. این مقادیر ممکن است دوربین‌های جداگانه را نشان دهند، یا ممکن است جهت‌هایی را نشان دهند که یک دوربین قابل تنظیم می‌تواند به سمت آن‌ها نشانه برود.

- `"user"`
  - : منبع ویدیو به سمت کاربر است؛ این شامل، به عنوان مثال، دوربین جلوی یک گوشی هوشمند می‌شود.
- `"environment"`
  - : منبع ویدیو رو به دور از کاربر است و بنابراین محیط اطراف او را نشان می‌دهد. این دوربین پشت گوشی هوشمند است.
- `"left"`
  - : منبع ویدیو رو به کاربر است اما به سمت چپ او؛ مانند دوربینی که به سمت کاربر نشانه رفته است اما از روی شانهٔ چپ او.
- `"right"`
  - : منبع ویدیو رو به کاربر است اما به سمت راست او؛ مانند دوربینی که به سمت کاربر نشانه رفته است اما از روی شانهٔ راست او.

## مثال‌ها

به مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.facingMode")}}
- {{domxref("MediaTrackSettings")}}