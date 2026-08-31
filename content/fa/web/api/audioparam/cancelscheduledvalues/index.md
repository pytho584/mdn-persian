---
title: "AudioParam: cancelScheduledValues() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/cancelScheduledValues"
translated_by: "n8n + AI"
---

---
title: "AudioParam: cancelScheduledValues() method"
short-title: cancelScheduledValues()
slug: Web/API/AudioParam/cancelScheduledValues
page-type: web-api-instance-method
browser-compat: api.AudioParam.cancelScheduledValues
---

{{ APIRef("Web Audio API") }}

متد `cancelScheduledValues()` از رابط {{ domxref("AudioParam") }} تمام تغییرات برنامه‌ریزی‌شده آینده را برای `AudioParam` لغو می‌کند.

## نحو

```js-nolint
cancelScheduledValues(startTime)
```

### پارامترها

- `startTime`
  - : یک عدد اعشاری (double) که زمان (به ثانیه) پس از ایجاد نخستین {{ domxref("AudioContext") }} را نشان می‌دهد که بعد از آن همه تغییرات برنامه‌ریزی‌شده لغو خواهند شد.

### مقدار بازگشتی

یک ارجاع به این شیء `AudioParam`. در برخی پیاده‌سازی‌های قدیمی‌تر، این متد {{jsxref('undefined')}} را برمی‌گرداند.

## مثال‌ها

```js
const gainNode = audioCtx.createGain();
gainNode.gain.setValueCurveAtTime(waveArray, audioCtx.currentTime, 2); // 'gain' is the AudioParam
gainNode.gain.cancelScheduledValues(audioCtx.currentTime);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)