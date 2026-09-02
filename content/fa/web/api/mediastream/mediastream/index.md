---
title: "MediaStream: MediaStream() constructor"
short-title: MediaStream()
slug: Web/API/MediaStream/MediaStream
page-type: web-api-constructor
browser-compat: api.MediaStream.MediaStream
---

{{APIRef("Media Capture and Streams")}}

سازندهٔ **`MediaStream()`** یک شیء {{domxref("MediaStream")}} تازه‌ساخته برمی‌گرداند که به‌عنوان مجموعه‌ای از trackهای رسانه‌ای عمل می‌کند؛ هر track با یک شیء {{domxref("MediaStreamTrack")}} نمایش داده می‌شود.

اگر پارامتری داده شود، trackهای مشخص‌شده به جریان جدید اضافه می‌شوند. در غیر این صورت، جریان هیچ trackی ندارد.

## نحو (Syntax)

```js-nolint
new MediaStream()
new MediaStream(stream)
new MediaStream(tracks)
```

### پارامترها

- `stream` {{optional_inline}}
  - : یک شیء متفاوت {{domxref("MediaStream")}} که trackهای آن به‌طور خودکار به جریان تازه‌ساخته اضافه می‌شوند. این trackها از جریان اصلی حذف نمی‌شوند، بنابراین هر دو جریان آن‌ها را به اشتراک می‌گذارند.
- `tracks` {{optional_inline}}
  - : یک {{jsxref("Array")}} از اشیاء {{domxref("MediaStreamTrack")}}، یکی برای هر track که باید به جریان اضافه شود.

### مقدار بازگشتی

یک شیء {{domxref("MediaStream")}} تازه‌ساخته که یا خالی است یا شامل trackهای ارائه‌شده، در صورت وجود، می‌باشد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaStream")}}