---
title: "DecompressionStream: DecompressionStream() constructor"
short-title: DecompressionStream()
slug: Web/API/DecompressionStream/DecompressionStream
page-type: web-api-constructor
browser-compat: api.DecompressionStream.DecompressionStream
---

{{APIRef("Compression Streams API")}}{{AvailableInWorkers}}

سازندهٔ **`DecompressionStream()`** یک شیء جدید {{domxref("DecompressionStream")}} می‌سازد که یک جریان داده را فشرده‌زدایی می‌کند.

## نحو

```js-nolint
new DecompressionStream(format)
```

### پارامترها

- `format`
  - : یکی از قالب‌های فشرده‌سازی زیر:
    - `"brotli"`
      - : جریان داده را با استفاده از الگوریتم [Brotli](https://www.rfc-editor.org/info/rfc7932/) فشرده‌زدایی می‌کند.
    - `"gzip"`
      - : جریان داده را با استفاده از الگوریتم [GZIP](https://www.rfc-editor.org/info/rfc1952/) فشرده‌زدایی می‌کند.
    - `"deflate"`
      - : جریان داده را با استفاده از الگوریتم [DEFLATE](https://www.rfc-editor.org/info/rfc1950/) در قالب داده فشرده ZLIB فشرده‌زدایی می‌کند.
        قالب ZLIB شامل یک هدر (header) با اطلاعاتی در مورد روش فشرده‌سازی و اندازهٔ فشرده‌نشدهٔ داده‌ها، و همچنین یک checksum انتهایی برای بررسی یکپارچگی داده‌ها است.
    - `"deflate-raw"`
      - : جریان داده را با استفاده از الگوریتم [DEFLATE](https://www.rfc-editor.org/info/rfc1951/) بدون هدر و checksum انتهایی فشرده‌زدایی می‌کند.
    - `"zstd"`
      - : جریان داده را با استفاده از الگوریتم [ZSTD](https://datatracker.ietf.org/doc/html/rfc8478) فشرده‌زدایی می‌کند.

### استثناها

- {{jsxref("TypeError")}}
  - : در صورتی پرتاب می‌شود که قالب ارسال‌شده به سازنده پشتیبانی نشود.

## مثال‌ها

در این مثال، یک Blob فشرده‌شده با gzip فشرده‌زدایی می‌شود.

```js
const ds = new DecompressionStream("gzip");
const decompressedStream = blob.stream().pipeThrough(ds);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
