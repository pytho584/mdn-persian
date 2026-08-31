---
title: "AudioPlaybackStats: underrunEvents property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/underrunEvents"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: underrunEvents property"
short-title: underrunEvents
slug: Web/API/AudioPlaybackStats/underrunEvents
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioPlaybackStats.underrunEvents
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`underrunEvents`** در رابط {{domxref("AudioPlaybackStats")}} عددی است که نشان می‌دهد چند [underrun events](/en-US/docs/Web/API/AudioPlaybackStats#underrun_event) از زمان مقداردهی اولیه بافت صوتی رخ داده است.

## ارزش

یک عدد صحیح که تعداد رویدادهای underrun را نشان می‌دهد. مقدار اولیه آن `0` است.

## مثال‌ها

### استفاده پایه

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log number of underrun events
console.log(stats.underrunEvents);
```

برای مثال دقیق‌تر، همچنین به صفحه مرجع اصلی {{domxref("AudioPlaybackStats")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)