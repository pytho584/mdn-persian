---
title: "AudioWorkletGlobalScope: port"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletGlobalScope/port"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletGlobalScope: port"
short-title: port
slug: Web/API/AudioWorkletGlobalScope/port
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioWorkletGlobalScope.port
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

ویژگی فقط خواندنی **`port`** در رابط {{domxref("AudioWorkletGlobalScope")}} یک شی {{domxref("MessagePort")}} برمی‌گرداند که می‌توان از آن برای ارسال و دریافت پیام‌ها بین رشته اصلی و {{domxref("AudioWorklet")}} مرتبط استفاده کرد.

این امکان ارتباط ناهمگام سفارشی بین کد موجود در رشته اصلی و محدوده سراسری یک worklet صوتی را فراهم می‌کند، مانند ارسال داده‌های کنترلی یا تنظیمات سراسری.

## مقدار

شی {{domxref("MessagePort")}} که `AudioWorklet` و `AudioWorkletGlobalScope` مرتبط با آن را به هم متصل می‌کند.

## مثال‌ها

برای مثال‌ها به [`AudioWorkletNode.port`](/en-US/docs/Web/API/AudioWorkletNode/port#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [استفاده از AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)