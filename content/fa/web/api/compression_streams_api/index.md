---
title: "Compression Streams API"
---

---
title: Compression Streams API
slug: Web/API/Compression_Streams_API
page-type: web-api-overview
browser-compat: api.CompressionStream
---

{{DefaultAPISidebar("Compression Streams API")}}{{AvailableInWorkers}}

**Compression Streams API** یک رابط برنامه‌نویسی جاوااسکریپت برای فشرده‌سازی و از فشرده‌سازی خارج کردن جریان‌های داده با استفاده از قالب‌های gzip یا deflate فراهم می‌کند.

فشرده‌سازی داخلی به این معنی است که برنامه‌های جاوااسکریپت دیگر نیازی به گنجاندن یک کتابخانه فشرده‌سازی نخواهند داشت، که اندازه بارگیری برنامه را کوچک‌تر می‌کند.

از {{domxref("Response")}} در Fetch API می‌توان برای تبدیل جریان‌ها به موارد زیر استفاده کرد:

- {{jsxref("ArrayBuffer")}}
- {{domxref("Blob")}}
- {{jsxref("Uint8Array")}}
- {{jsxref("String")}}
- JSON

## رابط‌ها

- {{domxref("CompressionStream")}}
  - : جریانی از داده را فشرده می‌کند.
- {{domxref("DecompressionStream")}}
  - : جریانی از داده را از حالت فشرده خارج می‌کند.

## مثال‌ها

در این مثال، یک جریان با استفاده از فشرده‌سازی gzip فشرده می‌شود.

```js
const compressedReadableStream = inputReadableStream.pipeThrough(
  new CompressionStream("gzip"),
);
```

در مثال زیر، یک تابع یک blob را با استفاده از gzip از حالت فشرده خارج می‌کند.

```js
async function DecompressBlob(blob) {
  const ds = new DecompressionStream("gzip");
  const decompressedStream = blob.stream().pipeThrough(ds);
  return await new Response(decompressedStream).blob();
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}