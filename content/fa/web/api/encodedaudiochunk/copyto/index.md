---
title: "EncodedAudioChunk: copyTo() method"
short-title: copyTo()
slug: Web/API/EncodedAudioChunk/copyTo
page-type: web-api-instance-method
browser-compat: api.EncodedAudioChunk.copyTo
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`copyTo()`** در رابط {{domxref("EncodedAudioChunk")}}، داده‌های صوتی رمزگذاری‌شدهٔ این قطعه را کپی می‌کند.

## نحو (Syntax)

```js-nolint
copyTo(destination)
```

### پارامترها

- `destination`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} که داده‌ها می‌توانند در آن کپی شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در مثال زیر، یک {{domxref("EncodedAudioChunk")}} ساخته شده و سپس کپی می‌شود.

```js
const init = {
  type: "key",
  data: audioBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedAudioChunk(init);

chunk.copyTo(newBuffer);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```