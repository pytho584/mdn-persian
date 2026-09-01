---
title: "DecompressionStream: readable property"
short-title: readable
slug: Web/API/DecompressionStream/readable
page-type: web-api-instance-property
browser-compat: api.DecompressionStream.readable
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`readable`** از رابط {{domxref("DecompressionStream")}} یک {{domxref("ReadableStream")}} برمی‌گرداند که داده‌های فشرده‌شده را به صورت قطعات {{jsxref("Uint8Array")}} منتشر می‌کند.

## مقدار

یک {{domxref("ReadableStream")}}.

## مثال‌ها

این مثال یک `DecompressionStream` ایجاد می‌کند که فشرده‌سازی gzip را انجام می‌دهد. مقداری داده باینری فشرده شده را در جریان `writable` می‌نویسد، سپس داده‌های فشرده‌شده را از جریان `readable` می‌خواند و به صورت متن UTF-8 رمزگشایی می‌کند.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("TransformStream.readable")}}