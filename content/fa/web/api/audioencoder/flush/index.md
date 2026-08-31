---
title: "AudioEncoder: flush() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/flush"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: flush() method"
short-title: flush()
slug: Web/API/AudioEncoder/flush
page-type: web-api-instance-method
browser-compat: api.AudioEncoder.flush
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`flush()`** از رابط {{domxref("AudioEncoder")}} یک Promise برمی‌گرداند که پس از تکمیل تمام پیام‌های در انتظار در صف، حل می‌شود.

## نحو

```js-nolint
flush()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با undefined حل می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر Promise به دلیل اینکه {{domxref("AudioEncoder.state","state")}} برابر `"configured"` نیست رد شود، پرتاب می‌شود.

## مثال‌ها

مثال زیر `AudioEncoder` را فلش می‌کند.

```js
AudioEncoder.flush();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}