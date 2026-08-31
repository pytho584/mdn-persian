---
title: "AudioPlaybackStats: averageLatency property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/averageLatency"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: averageLatency property"
short-title: averageLatency
slug: Web/API/AudioPlaybackStats/averageLatency
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioPlaybackStats.averageLatency
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`averageLatency`** در رابط {{domxref("AudioPlaybackStats")}} یک عدد است که نشان‌دهندهٔ میانگین تأخیر از زمان مقداردهی اولیهٔ زمینهٔ صوتی یا از آخرین باری است که {{domxref("AudioPlaybackStats.resetLatency()")}} فراخوانی شده است.

## مقدار

یک عدد اعشاری با دقت دوبرابر که میانگین تأخیر را بر حسب ثانیه نشان می‌دهد.

## مثال‌ها

### استفادهٔ پایه

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log average latency
console.log(stats.averageLatency);
```

همچنین به صفحهٔ اصلی مرجع {{domxref("AudioPlaybackStats")}} برای یک مثال کامل‌تر مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [رابط برنامه‌نویسی وب صوتی](/en-US/docs/Web/API/Web_Audio_API)