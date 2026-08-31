---
title: "AudioDecoder: decodeQueueSize property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/decodeQueueSize"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: decodeQueueSize property"
short-title: decodeQueueSize
slug: Web/API/AudioDecoder/decodeQueueSize
page-type: web-api-instance-property
browser-compat: api.AudioDecoder.decodeQueueSize
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`decodeQueueSize`** در رابط {{domxref("AudioDecoder")}} تعداد درخواست‌های رمزگشایی در انتظار در صف را برمی‌گرداند.

## مقدار

یک عدد صحیح شامل تعداد درخواست‌ها.

## مثال‌ها

مثال زیر اندازه صف را در کنسول چاپ می‌کند.

```js
console.log(AudioDecoder.decodeQueueSize);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}