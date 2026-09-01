---
title: "EncodedVideoChunk: EncodedVideoChunk() constructor"
short-title: EncodedVideoChunk()
slug: Web/API/EncodedVideoChunk/EncodedVideoChunk
page-type: web-api-constructor
browser-compat: api.EncodedVideoChunk.EncodedVideoChunk
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

سازندهٔ **`EncodedVideoChunk()`** یک شیء {{domxref("EncodedVideoChunk")}} جدید می‌سازد که یک تکه ویدیوی کدگذاری‌شده را نمایش می‌دهد.

## نحو

```js-nolint
new EncodedVideoChunk(options)
```

### پارامترها

- `options`
  - : یک شیء شامل اعضای زیر:
    - `type`
      - : نشان می‌دهد که آیا این تکه، یک تکه کلیدی است که برای کدگذاری به فریم‌های دیگر وابسته نیست. یکی از موارد زیر:
        - `"key"`
          - : داده یک تکه کلیدی است.
        - `"delta"`
          - : داده یک تکه کلیدی نیست.
    - `timestamp`
      - : یک عدد صحیح که زمان‌نمای ویدیو را به میکروثانیه نشان می‌دهد.
    - `duration`
      - : یک عدد صحیح که طول ویدیو را به میکروثانیه نشان می‌دهد.
    - `data`
      - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}} یا یک {{jsxref("DataView")}} حاوی داده ویدیو.
    - `transfer`
      - : آرایه‌ای از {{jsxref("ArrayBuffer")}}ها که `EncodedVideoChunk` آن‌ها را جدا کرده و مالکیتشان را بر عهده می‌گیرد. اگر آرایه شامل {{jsxref("ArrayBuffer")}} پشتیبان `data` باشد، `EncodedVideoChunk` مستقیماً از آن بافر استفاده می‌کند و آن را کپی نمی‌کند.

## مثال‌ها

در مثال زیر، یک `EncodedVideoChunk` جدید ساخته می‌شود.

```js
const init = {
  type: "key",
  data: videoBuffer,
  timestamp: 23000000,
  duration: 2000000,
  transfer: [videoBuffer],
};
chunk = new EncodedVideoChunk(init);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
