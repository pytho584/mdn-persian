---
title: "AudioParam: minValue property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/minValue"
translated_by: "n8n + AI"
---

---
title: "AudioParam: minValue property"
short-title: minValue
slug: Web/API/AudioParam/minValue
page-type: web-api-instance-property
browser-compat: api.AudioParam.minValue
---

{{APIRef("Web Audio API")}}

خاصیت فقط خواندنی **`minValue`** از رابط {{domxref("AudioParam")}}، حداقل مقدار ممکن برای محدوده اسمی (موثر) پارامتر را نشان می‌دهد.

## مقدار

یک {{jsxref("Number")}} از نوع اعشاری که حداقل مقدار مجاز برای محدوده اسمی پارامتر را مشخص می‌کند.

مقدار پیش‌فرض `minValue`، حداقل مقدار اعشاری تک‌دقت منفی است (-340,282,346,638,528,859,811,704,183,484,516,925,440).

## مثال‌ها

```js
const audioCtx = new AudioContext();
const gainNode = audioCtx.createGain();
console.log(gainNode.gain.minValue); // -3.4028234663852886e38
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioParam.maxValue")}}