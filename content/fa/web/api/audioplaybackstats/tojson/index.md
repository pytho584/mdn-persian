---
title: "AudioPlaybackStats: toJSON() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/toJSON"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: toJSON() method"
short-title: toJSON()
slug: Web/API/AudioPlaybackStats/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.AudioPlaybackStats.toJSON
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

متد **`toJSON()`** از رابط {{domxref("AudioPlaybackStats")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ یک نمایش JSON از شیء {{domxref("AudioPlaybackStats")}} را برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("AudioPlaybackStats")}} است.

## مثال‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `stats.toJSON()` یک نمایش JSON از شیء `AudioPlaybackStats` را برمی‌گرداند.

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log playbackStats JSON
console.log(stats.toJSON());
```

این یک شیء JSON به شکل زیر را ثبت می‌کند:

```json
{
  "underrunDuration": 0,
  "underrunEvents": 0,
  "totalDuration": 68.252138,
  "averageLatency": 0.01863,
  "minimumLatency": 0,
  "maximumLatency": 0.018654
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(stats)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)