---
title: "MediaSource: removeSourceBuffer() method"
short-title: removeSourceBuffer()
slug: Web/API/MediaSource/removeSourceBuffer
page-type: web-api-instance-method
browser-compat: api.MediaSource.removeSourceBuffer
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`removeSourceBuffer()`** در رابط {{domxref("MediaSource")}}، {{domxref("SourceBuffer")}} داده‌شده را از {{domxref("SourceBufferList")}} مرتبط با این شیء `MediaSource` حذف می‌کند.

## نحو (Syntax)

```js-nolint
removeSourceBuffer(sourceBuffer)
```

### پارامترها

- `sourceBuffer`
  - : شیء {{domxref("SourceBuffer")}} که باید حذف شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `sourceBuffer` ارائه‌شده در {{domxref("MediaSource.sourceBuffers")}} وجود نداشته باشد، پرتاب می‌شود.

## مثال‌ها

```js
for (let i = 0; i < 10; i++) {
  const sourceBuffer = mediaSource.addSourceBuffer(mimeCodec);
}

mediaSource.removeSourceBuffer(mediaSource.sourceBuffers[0]);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}