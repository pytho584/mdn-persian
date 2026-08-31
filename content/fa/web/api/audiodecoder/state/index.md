---
title: "AudioDecoder: state property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/state"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: state property"
short-title: state
slug: Web/API/AudioDecoder/state
page-type: web-api-instance-property
browser-compat: api.AudioDecoder.state
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`state`** در رابط {{domxref("AudioDecoder")}} وضعیت فعلی کدک زیرین را برمی‌گرداند.

## مقدار

رشته‌ای شامل یکی از مقادیر زیر:

- `"unconfigured"`
  - : کدک برای رمزگشایی پیکربندی نشده است.
- `"configured"`
  - : کدک پیکربندی معتبری دارد و آماده است.
- `"closed"`
  - : کدک دیگر قابل استفاده نیست و منابع سیستم آزاد شده‌اند.

## مثال‌ها

مثال زیر وضعیت `AudioDecoder` را در کنسول چاپ می‌کند.

```js
console.log(AudioDecoder.state);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}