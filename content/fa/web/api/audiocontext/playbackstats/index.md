---
title: "AudioContext: playbackStats property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/playbackStats"
translated_by: "n8n + AI"
---

---
title: "AudioContext: playbackStats property"
short-title: playbackStats
slug: Web/API/AudioContext/playbackStats
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioContext.playbackStats
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`playbackStats`** از رابط {{domxref("AudioContext")}} یک شیء {{domxref("AudioPlaybackStats")}} برمی‌گرداند که دسترسی به آمار مدت، کمبود داده (underrun) و تأخیر را برای `AudioContext` فراهم می‌کند. این آمار به شما امکان می‌دهد تأخیر صوتی و خطاهای پخش را اندازه‌گیری کنید.

امکان دریافت تأخیر پخش بی‌درنگ زمینه از طریق ویژگی {{domxref("AudioContext.outputLatency")}} وجود دارد؛ با این حال، `playbackStats` دسترسی به آمار جزئی‌تری فراهم می‌کند که به مرور زمان به‌روزرسانی می‌شوند، از جمله میانگین، حداقل و حداکثر تأخیر.

## مقدار

یک شیء {{domxref("AudioPlaybackStats")}}.

## مثال‌ها

### استفادهٔ پایه

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log average latency
console.log(stats.averageLatency);
```

برای مثالی کامل‌تر، به صفحهٔ مرجع اصلی {{domxref("AudioPlaybackStats")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)