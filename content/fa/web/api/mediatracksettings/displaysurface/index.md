---
title: "MediaTrackSettings: displaySurface property"
short-title: displaySurface
slug: Web/API/MediaTrackSettings/displaySurface
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.displaySurface_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`displaySurface`** در فرهنگ لغت {{domxref("MediaTrackSettings")}} نوع سطح نمایش را که در حال ضبط است مشخص می‌کند.

## مقدار

مقدار `displaySurface` یک رشته است که از نوع شمارشی `DisplayCaptureSurfaceType` گرفته می‌شود و می‌تواند یکی از موارد زیر باشد:

- `browser`
  - : مسیر ویدیویی جریان، محتوای کامل یک تب مرورگر را نشان می‌دهد که کاربر در طول فراخوانی {{domxref("MediaDevices.getDisplayMedia","getDisplayMedia()")}} آن را انتخاب کرده است.
- `monitor`
  - : مسیر ویدیویی موجود در جریان، محتوای کامل یک یا چند صفحه از کاربر را نشان می‌دهد. هر فضای خالی (اگر نمایشگرها ابعاد متفاوتی داشته باشند) با پس‌زمینه‌ای که عامل کاربر (user agent) انتخاب می‌کند پر می‌شود.
- `window`
  - : مسیر ویدیویی جریان، محتوای یک پنجره واحد را که کاربر انتخاب کرده است نشان می‌دهد. این پنجره می‌تواند از هر برنامه‌ای باشد، نه لزوماً فقط از داخل عامل کاربر.

توجه داشته باشید که همه عامل‌های کاربر از همه این انواع سطح پشتیبانی نمی‌کنند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}