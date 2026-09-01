---
title: "DynamicsCompressorNode: release property"
short-title: release
slug: Web/API/DynamicsCompressorNode/release
page-type: web-api-instance-property
browser-compat: api.DynamicsCompressorNode.release
---

{{ APIRef("Web Audio API") }}

ویژگی `release` در رابط {{ domxref("DynamicsCompressorNode") }} یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که مدت‌زمان لازم برای افزایش بهره (gain) به اندازهٔ ۱۰ دسیبل را بر حسب ثانیه نشان می‌دهد. این ویژگی مشخص می‌کند که با کاهش حجم صدا، سیگنال با چه سرعتی تطبیق داده می‌شود.

مقدار پیش‌فرض ویژگی `release` برابر با `0.25` است و می‌توان آن را بین `0` و `1` تنظیم کرد.

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه {{domxref("AudioParam")}} بازگشتی فقط‌خواندنی (read-only) است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

```js
const audioCtx = new AudioContext();
const compressor = audioCtx.createDynamicsCompressor();
compressor.release.value = 0.25;
```

برای مشاهدهٔ کد مثال کامل‌تر به [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)