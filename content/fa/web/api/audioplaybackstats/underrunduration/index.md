---
title: "AudioPlaybackStats: underrunDuration property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/underrunDuration"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: underrunDuration property"
short-title: underrunDuration
slug: Web/API/AudioPlaybackStats/underrunDuration
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioPlaybackStats.underrunDuration
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

**`underrunDuration`** خاصیت فقط خواندنی رابط {{domxref("AudioPlaybackStats")}} است، عددی که مجموع مدت‌زمان [رخدادهای underrun](/en-US/docs/Web/API/AudioPlaybackStats#underrun_event) را از زمان راه‌اندازی زمینه صوتی نشان می‌دهد.

## مقدار

یک عدد ممیز شناور با دقت دوگانه که مدت‌زمان رخدادهای underrun را بر حسب ثانیه نشان می‌دهد. مقدار اولیه `0` است.

## مثال‌ها

### کاربرد پایه

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log total duration of underrun events
console.log(stats.underrunDuration);
```

برای یک مثال عمیق‌تر، به صفحه مرجع اصلی {{domxref("AudioPlaybackStats")}} نیز مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)