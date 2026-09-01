---
title: "EncodedVideoChunk: copyTo() method"
short-title: copyTo()
slug: Web/API/EncodedVideoChunk/copyTo
page-type: web-api-instance-method
browser-compat: api.EncodedVideoChunk.copyTo
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`copyTo()`** از رابط {{domxref("EncodedVideoChunk")}} یک قطعه از داده‌های ویدیوی کدگذاری شده را کپی می‌کند.

## نحو

```js-nolint
copyTo(destination)
```

### پارامترها

- `destination`
  - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}} یا یک {{jsxref("DataView")}} که داده‌ها می‌توانند در آن کپی شوند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

در مثال زیر، یک {{domxref("EncodedVideoChunk")}} ساخته شده و سپس کپی می‌شود.

```js
const init = {
  type: "key",
  data: videoBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedVideoChunk(init);

chunk.copyTo(newBuffer);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}