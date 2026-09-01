---
title: "DecompressionStream"
source: "https://developer.mozilla.org/en-US/docs/Web/API/DecompressionStream"
---

---
title: DecompressionStream
slug: Web/API/DecompressionStream
page-type: web-api-interface
browser-compat: api.DecompressionStream
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

**`DecompressionStream`** که بخشی از {{domxref('Compression Streams API','','',' ')}} است، یک جریان داده را از حالت فشرده خارج می‌کند. این رابط همان ساختار {{domxref("TransformStream")}} را دارد و می‌توان آن را در {{domxref("ReadableStream.pipeThrough()")}} و روش‌های مشابه به کار برد.

## سازنده

- {{domxref("DecompressionStream.DecompressionStream", "DecompressionStream()")}}
  - : یک نمونه جدید از `DecompressionStream` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("DecompressionStream.readable")}}
  - : نمونه {{domxref("ReadableStream")}} کنترل‌شده توسط این شیء را برمی‌گرداند.
- {{domxref("DecompressionStream.writable")}}
  - : نمونه {{domxref("WritableStream")}} کنترل‌شده توسط این شیء را برمی‌گرداند.

## مثال‌ها

در این مثال، یک blob با استفاده از فشرده‌سازی gzip از حالت فشرده خارج می‌شود.

```js
const ds = new DecompressionStream("gzip");
const decompressedStream = blob.stream().pipeThrough(ds);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("CompressionStream")}}
- {{domxref("TransformStream")}}