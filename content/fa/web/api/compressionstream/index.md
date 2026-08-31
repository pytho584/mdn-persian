---
title: "CompressionStream"
---

---
title: CompressionStream
slug: Web/API/CompressionStream
page-type: web-api-interface
browser-compat: api.CompressionStream
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

رابط **`CompressionStream`** از {{domxref('Compression Streams API','','',' ')}} یک جریان از داده‌ها را فشرده می‌کند. این رابط همان ساختار {{domxref("TransformStream")}} را پیاده‌سازی می‌کند و به آن اجازه می‌دهد در {{domxref("ReadableStream.pipeThrough()")}} و روش‌های مشابه استفاده شود.

## سازنده

- {{domxref("CompressionStream.CompressionStream", "CompressionStream()")}}
  - : یک `CompressionStream` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("CompressionStream.readable")}}
  - : نمونه {{domxref("ReadableStream")}} کنترل‌شده توسط این شیء را برمی‌گرداند.
- {{domxref("CompressionStream.writable")}}
  - : نمونه {{domxref("WritableStream")}} کنترل‌شده توسط این شیء را برمی‌گرداند.

## مثال‌ها

در این مثال، یک جریان با استفاده از فشرده‌سازی gzip فشرده می‌شود.

```js
const compressedReadableStream = inputReadableStream.pipeThrough(
  new CompressionStream("gzip"),
);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DecompressionStream")}}
- {{domxref("TransformStream")}}