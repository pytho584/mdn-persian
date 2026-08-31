---
title: "AudioParam: defaultValue property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/defaultValue"
translated_by: "n8n + AI"
---

---
title: "AudioParam: defaultValue property"
short-title: defaultValue
slug: Web/API/AudioParam/defaultValue
page-type: web-api-instance-property
browser-compat: api.AudioParam.defaultValue
---

{{APIRef("Web Audio API")}}

**`defaultValue`** ویژگی فقط-خواندنی از رابط {{ domxref("AudioParam") }} مقدار اولیه ویژگی‌ها را مطابق با آنچه توسط {{domxref("AudioNode")}} خاصی که `AudioParam` را ایجاد کرده است، نشان می‌دهد.

## مقدار

یک {{jsxref("Number")}} ممیز شناور.

## مثال‌ها

```js
const audioCtx = new AudioContext();
const gainNode = audioCtx.createGain();
const defaultVal = gainNode.gain.defaultValue;
console.log(defaultVal); // 1
console.log(defaultVal === gainNode.gain.value); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)