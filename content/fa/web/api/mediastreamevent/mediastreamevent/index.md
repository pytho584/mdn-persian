---
title: "MediaStreamEvent: MediaStreamEvent() constructor"
short-title: MediaStreamEvent()
slug: Web/API/MediaStreamEvent/MediaStreamEvent
page-type: web-api-constructor
status:
  - deprecated
  - non-standard
browser-compat: api.MediaStreamEvent.MediaStreamEvent
---

{{APIRef("WebRTC")}}{{Deprecated_Header}}{{Non-standard_Header}}

سازندهٔ **`MediaStreamEvent()`** یک شیء جدید از نوع {{domxref("MediaStreamEvent")}} می‌سازد.

## سینتکس

```js-nolint
 new MediaStreamEvent(type, options)
```

### مقادیر

- `type`
  - : رشته‌ای است با نام رویداد، مانند `addstream` یا `removestream`.
- `options`
  - : یک شیء که علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}، می‌تواند ویژگی زیر را داشته باشد:
    - `stream`
      - : یک {{domxref("MediaStream")}} که جریان موردنظر رویداد را نشان می‌دهد.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("MediaStreamEvent")}}.

## مثال

```js
// s is a MediaStream
const event = new MediaStreamEvent("addstream", { stream: s });
```

## مشخصات

_این ویژگی دیگر بخشی از هیچ مشخصاتی نیست._

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebRTC](/en-US/docs/Web/API/WebRTC_API)