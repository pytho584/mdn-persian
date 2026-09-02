---
title: "MediaStreamTrackProcessor: MediaStreamTrackProcessor() constructor"
short-title: MediaStreamTrackProcessor()
slug: Web/API/MediaStreamTrackProcessor/MediaStreamTrackProcessor
page-type: web-api-constructor
browser-compat: api.MediaStreamTrackProcessor.MediaStreamTrackProcessor
---

{{APIRef("Insertable Streams for MediaStreamTrack API")}}

سازنده **`MediaStreamTrackProcessor()`** یک شیء جدید {{domxref("MediaStreamTrackProcessor")}} می‌سازد که منبع یک شیء {{domxref("MediaStreamTrack")}} ویدئو را مصرف کرده و جریانی از {{domxref("VideoFrame")}}ها تولید می‌کند.

## Syntax

```js-nolint
new MediaStreamTrackProcessor(options)
```

### Parameters

- `options`
  - : یک شیء با ویژگی‌های زیر:
    - `track`
      - : یک {{domxref("MediaStreamTrack")}}.
    - `maxBufferSize` {{optional_inline}}
      - : یک عدد صحیح که حداکثر تعداد فریم‌های رسانه‌ای را که بافر می‌شوند مشخص می‌کند.

## Examples

در مثال زیر یک `MediaStreamTrackProcessor` جدید ساخته می‌شود.

```js
const trackProcessor = new MediaStreamTrackProcessor({ track: videoTrack });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```