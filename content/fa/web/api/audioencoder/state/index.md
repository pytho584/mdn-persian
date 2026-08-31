---
title: "AudioEncoder: state property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/state"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: state property"
short-title: state
slug: Web/API/AudioEncoder/state
page-type: web-api-instance-property
browser-compat: api.AudioEncoder.state
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

خاصیت فقط خواندنی **`state`** از رابط {{domxref("AudioEncoder")}} وضعیت فعلی کدک زیرین را برمی‌گرداند.

## مقدار

یک رشته شامل یکی از مقادیر زیر:

- `"unconfigured"`
  - : کدک برای رمزگشایی پیکربندی نشده است.
- `"configured"`
  - : کدک دارای پیکربندی معتبر و آماده است.
- `"closed"`
  - : کدک دیگر قابل استفاده نیست و منابع سیستم آزاد شده‌اند.

## مثال‌ها

مثال زیر وضعیت `AudioEncoder` را در کنسول چاپ می‌کند.

```js
console.log(AudioEncoder.state);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}