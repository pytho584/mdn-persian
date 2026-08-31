---
title: "AudioPlaybackStats: minimumLatency property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/minimumLatency"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: minimumLatency property"
short-title: minimumLatency
slug: Web/API/AudioPlaybackStats/minimumLatency
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioPlaybackStats.minimumLatency
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`minimumLatency`** از رابط {{domxref("AudioPlaybackStats")}} یک عدد است که کمترین تأخیر (latency) را از زمان راه‌اندازی بافت صوتی یا از زمان آخرین فراخوانی {{domxref("AudioPlaybackStats.resetLatency()")}} نشان می‌دهد.

## مقدار

یک عدد ممیز شناور با دقت دوگانه که کمترین تأخیر را بر حسب ثانیه نشان می‌دهد. مقدار اولیه `0` است.

## مثال‌ها

### استفاده پایه

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log minimum latency
console.log(stats.minimumLatency);
```

همچنین به صفحه اصلی مرجع {{domxref("AudioPlaybackStats")}} برای یک مثال جامع‌تر مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)