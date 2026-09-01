---
title: "DynamicsCompressorNode: threshold property"
short-title: threshold
slug: Web/API/DynamicsCompressorNode/threshold
page-type: web-api-instance-property
browser-compat: api.DynamicsCompressorNode.threshold
---

{{ APIRef("Web Audio API") }}

ویژگی `threshold` در رابط {{ domxref("DynamicsCompressorNode") }} یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که مقدار دسیبلی را مشخص می‌کند که اگر سیگنال از آن بالاتر برود، فشرده‌سازی شروع به اثرگذاری می‌کند.

مقدار پیش‌فرض ویژگی `threshold`، `24-` است و می‌توان آن را بین `100-` و `0` تنظیم کرد.

![The threshold attribute has no effect on signals lowers than its value, but induce volume reduction on signal stronger than its value.](webaudiothreshold.png)

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه {{domxref("AudioParam")}} بازگردانده‌شده فقط‌خواندنی است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

```js
const audioCtx = new AudioContext();
const compressor = audioCtx.createDynamicsCompressor();
compressor.threshold.value = -50;
```

برای کد مثال کامل‌تر به [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)