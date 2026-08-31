---
title: "CompressionStream: CompressionStream() constructor"
short-title: CompressionStream()
slug: Web/API/CompressionStream/CompressionStream
page-type: web-api-constructor
browser-compat: api.CompressionStream.CompressionStream
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

سازندهٔ **`CompressionStream()`** یک شیء جدید {{domxref("CompressionStream")}} می‌سازد که یک جریان داده را فشرده می‌کند.

## نحو (Syntax)

```js-nolint
new CompressionStream(format)
```

### پارامترها

- `format`
  - : یکی از قالب‌های فشرده‌سازی مجاز زیر:
    - `"gzip"`
      - : جریان را با استفاده از قالب [GZIP](https://www.rfc-editor.org/info/rfc1952/) فشرده می‌کند.
    - `"brotli"`
      - : جریان را با استفاده از الگوریتم [Brotli](https://www.rfc-editor.org/info/rfc7932/) فشرده می‌کند.
    - `"deflate"`
      - : جریان را با استفاده از الگوریتم [DEFLATE](https://www.rfc-editor.org/info/rfc1950/) در قالب دادهٔ فشردهٔ ZLIB فشرده می‌کند.
        قالب ZLIB شامل یک سربرگ با اطلاعاتی دربارهٔ روش فشرده‌سازی و اندازهٔ بدون فشرده‌سازی داده‌ها، و یک جمع‌بندی انتهایی (checksum) برای تأیید صحت داده‌ها است.
    - `"deflate-raw"`
      - : جریان را با استفاده از الگوریتم [DEFLATE](https://www.rfc-editor.org/info/rfc1951/) بدون سربرگ و جمع‌بندی انتهایی فشرده می‌کند.
    - `"zstd"`
      - : جریان را با استفاده از الگوریتم [ZSTD](https://datatracker.ietf.org/doc/html/rfc8478) فشرده می‌کند.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر قالبی که به سازنده داده شده است پشتیبانی نشود، پرتاب می‌شود.

## مثال‌ها

در این مثال، یک جریان با استفاده از فشرده‌سازی gzip فشرده می‌شود.

```js
const compressedReadableStream = inputReadableStream.pipeThrough(
  new CompressionStream("gzip"),
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}