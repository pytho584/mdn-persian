---
title: "MediaStreamTrack: readyState property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/readyState"
---

---
title: "MediaStreamTrack: readyState property"
short-title: readyState
slug: Web/API/MediaStreamTrack/readyState
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.readyState
---

{{APIRef("Media Capture and Streams")}}

ویژگی فقط‌خواندنی **`readyState`** در رابط {{domxref("MediaStreamTrack")}} یک مقدار شمارشی برمی‌گرداند که وضعیت فعلی مسیر (track) را نشان می‌دهد.

## مقدار

یکی از مقادیر زیر را می‌گیرد:

- `"live"` که نشان می‌دهد یک ورودی متصل است و بهترین تلاش خود را برای ارائه‌ی داده‌های بلادرنگ انجام می‌دهد. در این حالت، خروجی داده را می‌توان با استفاده از ویژگی {{domxref("MediaStreamTrack.enabled")}} روشن یا خاموش کرد.
- `"ended"` که نشان می‌دهد ورودی دیگر داده‌ای ارائه نمی‌دهد و هرگز داده‌ی جدیدی ارائه نخواهد داد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط رسانه و جریان‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC](/en-US/docs/Web/API/WebRTC_API)
- رویداد {{domxref("MediaStreamTrack.ended_event", "ended")}}