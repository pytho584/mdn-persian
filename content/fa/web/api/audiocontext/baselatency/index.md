---
title: "AudioContext: baseLatency property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/baseLatency"
translated_by: "n8n + AI"
---

---
title: "AudioContext: baseLatency property"
short-title: baseLatency
slug: Web/API/AudioContext/baseLatency
page-type: web-api-instance-property
browser-compat: api.AudioContext.baseLatency
---

{{APIRef("Web Audio API")}}

ویژگی فقط‌خواندنی **`baseLatency`** از رابط {{domxref("AudioContext")}} یک عدد اعشاری برمی‌گرداند که نشان‌دهندهٔ تعداد ثانیه‌های تأخیر پردازشی است که توسط `AudioContext` هنگام عبور یک بافر صوتی از {{domxref("AudioDestinationNode")}} — یعنی انتهای گراف صوتی — به زیرسیستم صوتی سیستم میزبان برای پخش آماده می‌شود.

> [!NOTE]
> شما می‌توانید مقدار مشخصی از تأخیر را در حین {{domxref("AudioContext.AudioContext()", "زمان ساخت", "", "true")}} با استفاده از گزینهٔ `latencyHint` درخواست کنید، اما مرورگر ممکن است این گزینه را نادیده بگیرد.

## مقدار

یک عدد اعشاری که تأخیر پایه را بر حسب ثانیه نشان می‌دهد.

## مثال‌ها

```js
// default latency ("interactive")
const audioCtx1 = new AudioContext();
console.log(audioCtx1.baseLatency); // 0.00

// higher latency ("playback")
const audioCtx2 = new AudioContext({ latencyHint: "playback" });
console.log(audioCtx2.baseLatency); // 0.15
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)