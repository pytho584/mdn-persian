---
title: "ByteLengthQueuingStrategy: size() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ByteLengthQueuingStrategy/size"
translated_by: "n8n + AI"
short-title: size()
slug: Web/API/ByteLengthQueuingStrategy/size
page-type: web-api-instance-method
browser-compat: api.ByteLengthQueuingStrategy.size
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

متد **`size()`** از رابط {{domxref("ByteLengthQueuingStrategy")}}، ویژگی `byteLength` قطعه داده شده را بازمی‌گرداند.

## نحو

```js-nolint
size(chunk)
```

### پارامترها

- `chunk`
  - : یک قطعه از داده که در حال عبور از جریان است.

### مقدار بازگشتی

یک عدد صحیح که طول بایت قطعه داده شده را نشان می‌دهد.

## مثال‌ها

```js
const queuingStrategy = new ByteLengthQueuingStrategy({ highWaterMark: 1 });

const readableStream = new ReadableStream(
  {
    start(controller) {
      // …
    },
    pull(controller) {
      // …
    },
    cancel(err) {
      console.log("stream error:", err);
    },
  },
  queuingStrategy,
);

const size = queuingStrategy.size(chunk);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ByteLengthQueuingStrategy.ByteLengthQueuingStrategy", "ByteLengthQueuingStrategy()")}} constructor