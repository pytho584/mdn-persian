---
title: "MediaStreamTrackGenerator: MediaStreamTrackGenerator() constructor"
short-title: MediaStreamTrackGenerator()
slug: Web/API/MediaStreamTrackGenerator/MediaStreamTrackGenerator
page-type: web-api-constructor
status:
  - experimental
  - non-standard
browser-compat: api.MediaStreamTrackGenerator.MediaStreamTrackGenerator
---

{{APIRef("Insertable Streams for MediaStreamTrack API")}}{{SeeCompatTable}}{{Non-standard_Header}}

سازندهٔ **`MediaStreamTrackGenerator()`** یک شیء {{domxref("MediaStreamTrackGenerator")}} جدید می‌سازد که جریانی از فریم‌های رسانه را مصرف می‌کند و یک {{domxref("MediaStreamTrack")}} در اختیار می‌گذارد.

## نحو (Syntax)

```js-nolint
new MediaStreamTrackGenerator(options)
```

### پارامترها

- `options` {{Experimental_Inline}} {{Non-standard_Inline}}
  - : شیءای شامل ویژگی `kind` که یکی از رشته‌های زیر است:
    - `"audio"`
      - : مشخص می‌کند که جریان، شیءهای {{domxref("AudioTrack")}} را می‌پذیرد.
    - `"video"`
      - : مشخص می‌کند که جریان، شیءهای {{domxref("VideoTrack")}} را می‌پذیرد.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر `init.kind` برابر با `"video"` یا `"audio"` نباشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک `MediaStreamTrackGenerator` ویدیویی جدید ساخته می‌شود.

```js
const trackGenerator = new MediaStreamTrackGenerator({ kind: "video" });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [جریان‌های قابل درج برای MediaStreamTrack](https://developer.chrome.com/docs/capabilities/web-apis/mediastreamtrack-insertable-media-processing)