---
title: "CompressionStream: readable property"
short-title: readable
slug: Web/API/CompressionStream/readable
page-type: web-api-instance-property
browser-compat: api.CompressionStream.readable
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`readable`** از رابط {{domxref("CompressionStream")}} یک {{domxref("ReadableStream")}} برمی‌گرداند که داده‌های فشرده‌شده را به صورت تکه‌های {{jsxref("Uint8Array")}} منتشر می‌کند.

## مقدار

یک {{domxref("ReadableStream")}}.

## مثال‌ها

این مثال یک `CompressionStream` می‌سازد که فشرده‌سازی gzip را انجام می‌دهد. سپس داده‌های باینری را در جریان `writable` می‌نویسد و داده‌های فشرده‌شده را از جریان `readable` می‌خواند.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("TransformStream.readable")}}