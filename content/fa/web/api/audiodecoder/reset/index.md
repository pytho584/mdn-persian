---
title: "AudioDecoder: reset() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/reset"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: reset() method"
short-title: reset()
slug: Web/API/AudioDecoder/reset
page-type: web-api-instance-method
browser-compat: api.AudioDecoder.reset
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`reset()`** در رابط {{domxref("AudioDecoder")}} همهٔ حالت‌ها از جمله پیکربندی، پیام‌های کنترلی در صف پیام‌های کنترلی و همهٔ فراخوانی‌های در انتظار را بازنشانی می‌کند.

## نحو

```js-nolint
reset()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر، `AudioDecoder` را بازنشانی می‌کند.

```js
AudioDecoder.reset();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}