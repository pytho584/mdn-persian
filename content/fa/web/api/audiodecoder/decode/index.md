```
---
title: "AudioDecoder: decode() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/decode"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: decode() method"
short-title: decode()
slug: Web/API/AudioDecoder/decode
page-type: web-api-instance-method
browser-compat: api.AudioDecoder.decode
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`decode()`** از رابط {{domxref("AudioDecoder")}} یک پیام کنترلی را برای رمزگشایی یک تکه مشخص از صدا در صف قرار می‌دهد.

## نحو (Syntax)

```js-nolint
decode(chunk)
```

### پارامترها

- `chunk`
  - : یک شی {{domxref("EncodedAudioChunk")}} که نمایانگر یک تکه از صدای رمزگذاری‌شده است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("AudioDecoder.state","state")}} برابر `"configured"` نباشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر `chunk` به دلیل وابستگی به فریم‌های دیگر برای رمزگشایی قابل رمزگشایی نباشد، پرتاب می‌شود.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}
```