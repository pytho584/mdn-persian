```markdown
---
title: "MediaTrackSettings: volume property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MediaTrackSettings/volume"
---

---
title: "MediaTrackSettings: volume property"
short-title: volume
slug: Web/API/MediaTrackSettings/volume
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MediaStreamTrack.applyConstraints.volume_constraint
---

{{APIRef("Media Capture and Streams")}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی **`volume`** در فرهنگ‌لغت {{domxref("MediaTrackSettings")}}، یک عدد اعشاری با دقت دوگانه (double-precision floating-point) است که میزان بلندی صدای {{domxref("MediaStreamTrack")}} را در پیکربندی فعلی نشان می‌دهد. این مقدار عددی بین 0.0 (سکوت) تا 1.0 (حداکثر بلندی صدای پشتیبانی‌شده توسط دستگاه) است. این ویژگی به شما امکان می‌دهد تعیین کنید که برای مطابقت با محدودیت‌های مشخص‌شده‌تان برای این ویژگی چه مقداری انتخاب شده است؛ همان محدودیت‌هایی که در ویژگی {{domxref("MediaTrackConstraints.volume")}} هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domacro({{domxref("MediaStreamTrack.applyConstraints()")}} تعیین کرده‌اید.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.volume")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیت ناآشنایی را نادیده می‌گیرند.

## مقدار

یک عدد اعشاری با دقت دوگانه که بلندی صدای ترک صوتی را در پیکربندی فعلی، از 0.0 تا 1.0، نشان می‌دهد.

## مثال‌ها

به مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.volume")}}
- {{domxref("MediaTrackSettings")}}
```