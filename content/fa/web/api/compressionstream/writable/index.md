---
title: "CompressionStream: writable property"
short-title: writable
slug: Web/API/CompressionStream/writable
page-type: web-api-instance-property
browser-compat: api.CompressionStream.writable
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`writable`** از رابط {{domxref("CompressionStream")}} یک {{domxref("WritableStream")}} برمی‌گرداند که داده‌های فشرده‌نشده را به صورت تکه‌های {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} می‌پذیرد تا فشرده شوند.

## مقدار

یک {{domxref("WritableStream")}}.

## مثال‌ها

این مثال یک `CompressionStream` ایجاد می‌کند که فشرده‌سازی gzip را انجام می‌دهد. برخی داده‌های باینری را به جریان `writable` می‌نویسد، سپس داده‌های فشرده‌شده را از جریان `readable` می‌خواند.

```js
const stream = new CompressionStream("gzip");

// Write data to be compressed
const data = new TextEncoder().encode("Hello, world!");
const writer = stream.writable.getWriter();
writer.write(data);
writer.close();

// Read compressed data
const reader = stream.readable.getReader();
let done = false;
let output = [];
while (!done) {
  const result = await reader.read();
  if (result.value) {
    output.push(...result.value);
  }
  done = result.done;
}
console.log(new Uint8Array(output).toBase64()); // H4sIAAAAAAAAE/NIzcnJ11Eozy/KSVEEAObG5usNAAAA
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("TransformStream.writable")}}