---
title: "EncodedAudioChunk: EncodedAudioChunk() constructor"
short-title: EncodedAudioChunk()
slug: Web/API/EncodedAudioChunk/EncodedAudioChunk
page-type: web-api-constructor
browser-compat: api.EncodedAudioChunk.EncodedAudioChunk
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

سازندهٔ **`EncodedAudioChunk()`** یک شیء جدید {{domxref("EncodedAudioChunk")} می‌سازد که یک قطعه‌ی صوتی رمزگذاری‌شده را نمایش می‌دهد.

## Syntax

```js-nolint
new EncodedAudioChunk(options)
```

### Parameters

- `options`
  - : یک شیء حاوی اعضای زیر:
    - `type`
      - : مشخص می‌کند که آیا این قطعه، یک قطعه‌ی کلیدی است که برای رمزگشایی به فریم‌های دیگر وابسته نیست. یکی از مقادیر زیر:
        - `"key"`
          - : داده، یک قطعه‌ی کلیدی است.
        - `"delta"`
          - : داده، یک قطعه‌ی کلیدی نیست.
    - `timestamp`
      - : یک عدد صحیح که برچسب زمانی صدا را بر حسب میکروثانیه نشان می‌دهد.
    - `duration`
      - : یک عدد صحیح که طول صدا را بر حسب میکروثانیه نشان می‌دهد.
    - `data`
      - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} حاوی داده‌های صوتی.
    - `transfer`
      - : آرایه‌ای از {{jsxref("ArrayBuffer")}}ها که `EncodedAudioChunk` آن‌ها را detach می‌کند و مالکیت آن‌ها را بر عهده می‌گیرد. اگر آرایه شامل {{jsxref("ArrayBuffer")}} پشتیبانِ `data` باشد، `EncodedAudioChunk` مستقیماً از همان بافر استفاده می‌کند و آن را کپی نمی‌کند.

## Examples

در مثال زیر، یک `EncodedAudioChunk` جدید ساخته می‌شود.

```js
const init = {
  type: "key",
  data: audioBuffer,
  timestamp: 23000000,
  duration: 2000000,
  transfer: [audioBuffer],
};
chunk = new EncodedAudioChunk(init);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```