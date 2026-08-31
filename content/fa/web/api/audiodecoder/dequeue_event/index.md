---
title: "AudioDecoder: dequeue event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/dequeue_event"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: dequeue event"
short-title: dequeue
slug: Web/API/AudioDecoder/dequeue_event
page-type: web-api-event
browser-compat: api.AudioDecoder.dequeue_event
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رویداد **`dequeue`** از رابط {{domxref("AudioDecoder")}} برای نشان دادن کاهش در {{domxref("AudioDecoder.decodeQueueSize")}} فعال می‌شود.

این کار نیاز توسعه‌دهندگان به استفاده از نظرسنجی {{domxref("Window.setTimeout", "setTimeout()")}} برای تعیین زمان کاهش صف و زمان صف‌بندی کارهای بیشتر را از بین می‌برد.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("dequeue", (event) => { })

ondequeue = (event) => { }
```

## Example

```js
audioDecoder.addEventListener("dequeue", (event) => {
  // Queue up more decoding work
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}