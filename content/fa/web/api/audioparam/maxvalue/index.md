---
title: "AudioParam: maxValue property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/maxValue"
translated_by: "n8n + AI"
---

---
title: "AudioParam: maxValue property"
short-title: maxValue
slug: Web/API/AudioParam/maxValue
page-type: web-api-instance-property
browser-compat: api.AudioParam.maxValue
---

{{APIRef("Web Audio API")}}

ویژگی فقط‌خواندنی **`maxValue`** در رابط {{domxref("AudioParam")}}، حداکثر مقدار ممکن برای محدودهٔ اسمی (موثر) پارامتر را نشان می‌دهد.

## مقدار

یک {{jsxref("Number")}} ممیز شناور که حداکثر مقدار مجاز برای محدودهٔ اسمی پارامتر را نشان می‌دهد.

مقدار پیش‌فرض `maxValue`، حداکثر مقدار مثبت ممیز شناور تک‌دقتی است (+340,282,346,638,528,859,811,704,183,484,516,925,440).

## مثال‌ها

```js
const audioCtx = new AudioContext();
const gainNode = audioCtx.createGain();
console.log(gainNode.gain.maxValue); // 3.4028234663852886e38
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioParam.minValue")}}