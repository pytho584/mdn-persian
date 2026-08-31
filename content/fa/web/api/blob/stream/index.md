---
title: "Blob: stream() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/stream"
short-title: stream()
slug: Web/API/Blob/stream
page-type: web-api-instance-method
browser-compat: api.Blob.stream
translated_by: "n8n + AI"
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`stream()`** از رابط {{domxref("Blob")}} یک {{domxref("ReadableStream")}} برمی‌گرداند که با خواندن آن، داده‌های موجود در `Blob` بازگردانده می‌شود.

## نحو (Syntax)

```js-nolint
stream()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("ReadableStream")}} که با خواندن آن، محتویات `Blob` بازگردانده می‌شود.

## نکات استفاده

با `stream()` و {{domxref("ReadableStream")}} برگشتی، می‌توانید قابلیت‌های جالبی داشته باشید:

- با فراخوانی {{domxref("ReadableStream.getReader", "getReader()")}} روی استریم برگشتی، یک شیء برای خواندن داده‌های blob با استفاده از روش‌هایی مانند متد {{domxref("ReadableStreamDefaultReader.read", "read()")}} از رابط {{domxref("ReadableStreamDefaultReader")}} دریافت کنید.
- با فراخوانی متد {{domxref("ReadableStream.pipeTo", "pipeTo()")}} روی استریم برگشتی، داده‌های blob را به یک استریم قابل نوشتن (writable stream) هدایت کنید.
- با فراخوانی متد {{domxref("ReadableStream.tee", "tee()")}} روی استریم برگشتی، استریم خواندنی را **شاخه‌شاخه (tee)** کنید. این کار یک آرایه شامل دو شیء جدید `ReadableStream` برمی‌گرداند که هرکدام محتویات `Blob` را بازمی‌گردانند.
- با فراخوانی متد {{domxref("ReadableStream.pipeThrough", "pipeThrough()")}} روی استریم برگشتی، استریم را از طریق یک {{domxref("TransformStream")}} یا هر جفت خواندنی و نوشتنی دیگری هدایت کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Response.body")}}
- [API استریم‌ها](/en-US/docs/Web/API/Streams_API)