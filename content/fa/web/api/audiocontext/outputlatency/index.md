---
title: "AudioContext: outputLatency property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/outputLatency"
translated_by: "n8n + AI"
---

---
title: "AudioContext: outputLatency property"
short-title: outputLatency
slug: Web/API/AudioContext/outputLatency
page-type: web-api-instance-property
browser-compat: api.AudioContext.outputLatency
---

{{APIRef("Web Audio API")}}

ویژگی فقط‌خواندنی **`outputLatency`** در رابط {{domxref("AudioContext")}} تخمینی از تأخیر خروجی زمینه صوتی فعلی ارائه می‌دهد.

این زمان، بر حسب ثانیه، بین زمانی است که مرورگر یک بافر صوتی را از نمودار صوتی به زیرسیستم صوتی سیستم میزبان برای پخش می‌فرستد، و زمانی که اولین نمونه در بافر واقعاً توسط دستگاه خروجی صوتی پردازش می‌شود.

این مقدار بسته به پلتفرم و سخت‌افزار موجود متفاوت است.

## مقدار

یک double که تأخیر خروجی را بر حسب ثانیه نشان می‌دهد.

## مثال‌ها

```js
const audioCtx = new AudioContext();
console.log(audioCtx.outputLatency);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)