---
title: "MediaTrackSettings: cursor property"
short-title: cursor
slug: Web/API/MediaTrackSettings/cursor
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.cursor_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`cursor`** در دیکشنری {{domxref("MediaTrackSettings")}} مشخص می‌کند که آیا مکان‌نما باید به‌عنوان بخشی از ترک ویدیویی که در {{domxref("MediaStream")}} بازگردانده‌شده توسط {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} قرار می‌گیرد، ضبط شود یا خیر.

## مقدار

مقدار `cursor` از نوع رشته شمارشی `CursorCaptureConstraint` گرفته می‌شود و می‌تواند یکی از مقادیر زیر باشد:

- `always`
  - : مکان‌نمای ماوس همیشه باید در محتوای ویدیویی {{domxref("MediaStream")}} قابل مشاهده باشد، مگر اینکه ماوس به بیرون از ناحیه محتوا حرکت کرده باشد.
- `motion`
  - : اگر مکان‌نمای ماوس در حال حرکت باشد، همیشه در ویدیو گنجانده می‌شود، و برای مدت کوتاهی پس از توقف حرکت نیز همچنان در ویدیو باقی می‌ماند.
- `never`
  - : مکان‌نمای ماوس هرگز در ویدیوی به اشتراک گذاشته‌شده گنجانده نمی‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط برنامه‌نویسی Screen Capture](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از رابط برنامه‌نویسی Screen Capture](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}