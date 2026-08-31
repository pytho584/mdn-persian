---
title: "AudioEncoder: dequeue event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/dequeue_event"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: dequeue event"
short-title: dequeue
slug: Web/API/AudioEncoder/dequeue_event
page-type: web-api-event
browser-compat: api.AudioEncoder.dequeue_event
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رویداد **`dequeue`** از رابط {{domxref("AudioEncoder")}} برای اعلام کاهش در {{domxref("AudioEncoder.encodeQueueSize")}} فعال می‌شود.

این امر نیاز توسعه‌دهندگان به استفاده از یک بررسی دوره‌ای با {{domxref("Window.setTimeout", "setTimeout()")}} برای تعیین اینکه چه زمانی صف کاهش یافته و کار بیشتری باید در صف قرار گیرد را از بین می‌برد.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("dequeue", (event) => { })

ondequeue = (event) => { }
```

## مثال

```js
audioEncoder.addEventListener("dequeue", (event) => {
  // Queue up more encoding work
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}