---
title: "DynamicsCompressorNode: attack property"
---

---
title: "DynamicsCompressorNode: attack property"
short-title: attack
slug: Web/API/DynamicsCompressorNode/attack
page-type: web-api-instance-property
browser-compat: api.DynamicsCompressorNode.attack
---

{{ APIRef("Web Audio API") }}

ویژگی `attack` در رابط {{ domxref("DynamicsCompressorNode") }} یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که مدت زمان لازم (به ثانیه) برای کاهش بهره به اندازه ۱۰ دسیبل را نشان می‌دهد. این ویژگی مشخص می‌کند که با افزایش حجم سیگنال، سیگنال با چه سرعتی تطبیق داده شود.

مقدار پیش‌فرض ویژگی `attack` برابر با `0.003` است و می‌توان آن را بین `0` و `1` تنظیم کرد.

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه {{domxref("AudioParam")}} بازگردانده‌شده فقط‌خواندنی است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

```js
const audioCtx = new AudioContext();
const compressor = audioCtx.createDynamicsCompressor();
compressor.attack.value = 0;
```

برای نمونه‌کدهای کامل‌تر، [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)