---
title: "AudioEncoder: encode() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/encode"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: encode() method"
short-title: encode()
slug: Web/API/AudioEncoder/encode
page-type: web-api-instance-method
browser-compat: api.AudioEncoder.encode
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`encode()`** از رابط {{domxref("AudioEncoder")}} یک پیام کنترلی برای رمزگذاری یک شیء {{domxref("AudioData")}} در صف قرار می‌دهد.

## سینتکس

```js-nolint
encode(data)
```

### پارامترها

- `data`
  - : یک شیء {{domxref("AudioData")}}.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("AudioEncoder.state","state")}} برابر با `"configured"` نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر شیء `AudioData` [منتقل شده](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک شیء `AudioData` به `encode` ارسال می‌شود.

```js
encoder.encode(data);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}