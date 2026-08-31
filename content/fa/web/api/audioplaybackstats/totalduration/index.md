---
title: "AudioPlaybackStats: totalDuration property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/totalDuration"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: totalDuration property"
short-title: totalDuration
slug: Web/API/AudioPlaybackStats/totalDuration
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioPlaybackStats.totalDuration
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`totalDuration`** در رابط {{domxref("AudioPlaybackStats")}} یک عدد است که مدت‌زمان کل همه فریم‌های صوتی را از زمانی که زمینه صوتی مقداردهی شده است، نشان می‌دهد.

## مقدار

یک عدد ممیز شناور با دقت دوگانه که مدت‌زمان کل همه فریم‌های صوتی را بر حسب ثانیه نشان می‌دهد. مقدار اولیه `0` است.

## نمونه‌ها

### استفاده پایه

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log total duration
console.log(stats.totalDuration);
```

برای یک مثال دقیق‌تر، به صفحه مرجع اصلی {{domxref("AudioPlaybackStats")}} نیز مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)