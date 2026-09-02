---
title: "MediaTrackSettings: channelCount property"
short-title: channelCount
slug: Web/API/MediaTrackSettings/channelCount
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.channelCount_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`channelCount`** در {{domxref("MediaTrackSettings")}} یک عدد صحیح است که نشان می‌دهد {{domxref("MediaStreamTrack")}} در حال حاضر برای چند کانال صوتی پیکربندی شده است. به کمک این ویژگی می‌توانید ببینید برای برآوردن محدودیت‌های اعلام‌شده برای مقدار این ویژگی، چه مقداری انتخاب شده است. این محدودیت‌ها همان‌هایی هستند که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} از طریق ویژگی {{domxref("MediaTrackConstraints.channelCount")}} مشخص کرده بودید.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.channelCount")}} که در نتیجهٔ فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا نه. با این حال، معمولاً این کار ضروری نیست؛ زیرا مرورگرها محدودیت‌هایی را که برایشان ناآشنا هستند نادیده می‌گیرند.

## مقدار

مقدار این ویژگی یک عدد صحیح است که تعداد کانال‌های صوتی موجود در MediaStreamTrack را مشخص می‌کند. مقدار ۱ نشان‌دهندهٔ صدای تک‌کاناله (mono)، مقدار ۲ نشان‌دهندهٔ صدای استریو و به همین ترتیب است.

## مثال‌ها

برای مشاهدهٔ یک مثال کاربردی، نمونهٔ [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.channelCount")}}
- {{domxref("MediaTrackSettings")}}