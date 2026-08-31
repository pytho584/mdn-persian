---
title: "AudioWorkletProcessor: port property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletProcessor/port"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletProcessor: port property"
short-title: port
slug: Web/API/AudioWorkletProcessor/port
page-type: web-api-instance-property
browser-compat: api.AudioWorkletProcessor.port
---

{{APIRef("Web Audio API")}}

ویژگی **`port`** فقط‌خواندنی رابط {{domxref("AudioWorkletProcessor")}}، {{domxref("MessagePort")}} مرتبط را برمی‌گرداند. از آن می‌توان برای برقراری ارتباط بین پردازنده و {{domxref("AudioWorkletNode")}} متعلق به آن استفاده کرد.

> [!NOTE]
> پورت در انتهای دیگر کانال تحت ویژگی {{domxref("AudioWorkletNode.port", "port")}} گره در دسترس است.

## مقدار

شیء {{domxref("MessagePort")}} که `AudioWorkletProcessor` و `AudioWorkletNode` مرتبط را به هم متصل می‌کند.

## مثال‌ها

برای کد نمونه، [`AudioWorkletNode.port`](/en-US/docs/Web/API/AudioWorkletNode/port#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)