---
title: "DecompressionStream: writable property"
short-title: writable
slug: Web/API/DecompressionStream/writable
page-type: web-api-instance-property
browser-compat: api.DecompressionStream.writable
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`writable`** از رابط {{domxref("DecompressionStream")}} یک {{domxref("WritableStream")}} را برمی‌گرداند که داده‌های فشرده‌شده را برای فشرده‌گشایی (decompression) به صورت تکه‌های {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} می‌پذیرد.

## مقدار

یک {{domxref("WritableStream")}}.

## مثال‌ها

این مثال یک `DecompressionStream` ایجاد می‌کند که فشرده‌گشایی gzip را انجام می‌دهد. مقداری داده‌ی باینری فشرده را به جریان `writable` می‌نویسد، سپس داده‌های فشرده‌گشایی‌شده را از جریان `readable` می‌خواند و به صورت متن UTF-8 رمزگشایی می‌کند.

```js
const stream = new DecompressionStream("gzip");

// Write data to be compressed
const data = Uint8Array.fromBase64(
  "H4sIAAAAAAAAE/NIzcnJ11Eozy/KSVEEAObG5usNAAAA",
);
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
console.log(new TextDecoder().decode(new Uint8Array(output))); // Hello, world!
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("TransformStream.writable")}}