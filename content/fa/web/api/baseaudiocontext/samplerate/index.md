---
title: "BaseAudioContext: sampleRate property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/sampleRate"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: sampleRate property"
short-title: sampleRate
slug: Web/API/BaseAudioContext/sampleRate
page-type: web-api-instance-property
browser-compat: api.BaseAudioContext.sampleRate
---

{{ APIRef("Web Audio API") }}

ویژگی `sampleRate` از رابط {{domxref("BaseAudioContext")}} یک عدد اعشاری برمی‌گرداند که نرخ نمونه‌برداری، بر حسب نمونه در ثانیه، مورد استفاده تمام گره‌ها در این زمینه صوتی را نشان می‌دهد. این محدودیت به این معناست که مبدل‌های نرخ نمونه‌برداری پشتیبانی نمی‌شوند.

## مقدار

یک عدد اعشاری که نرخ نمونه‌برداری زمینه صوتی را بر حسب نمونه در ثانیه نشان می‌دهد.

## مثال‌ها

> [!NOTE]
> برای یک مثال کامل از پیاده‌سازی Web Audio، یکی از نمونه‌های Web Audio ما را در [MDN GitHub repo](https://github.com/mdn/webaudio-examples) ببینید. سعی کنید `audioCtx.sampleRate` را در کنسول مرورگر خود وارد کنید.

```js
const audioCtx = new AudioContext();
// Older webkit/blink browsers require a prefix

// …

console.log(audioCtx.sampleRate);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)