---
title: "MediaStream: clone() method"
short-title: clone()
slug: Web/API/MediaStream/clone
page-type: web-api-instance-method
browser-compat: api.MediaStream.clone
---

{{APIRef("Media Capture and Streams")}}

متد **`clone()`** در رابط {{domxref("MediaStream")}} یک کپی از `MediaStream` ایجاد می‌کند. این شیء `MediaStream` جدید یک {{domxref("MediaStream.id", "id")}} یکتا و جدید دارد و شامل کپی‌هایی از هر {{domxref("MediaStreamTrack")}} است که در `MediaStream` اصلی (همان‌که روی آن `clone()` فراخوانی شده) وجود دارد.

## Syntax

```js-nolint
clone()
```

### Parameters

هیچ.

### Return value

یک نمونه جدید از {{domxref("MediaStream")}} که دارای شناسه یکتای جدید است و شامل کپی‌هایی از هر {{domxref("MediaStreamTrack")}} موجود در `MediaStream` اصلی (همان‌که روی آن `clone()` فراخوانی شده) می‌باشد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}