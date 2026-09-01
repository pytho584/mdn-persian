---
title: "DynamicsCompressorNode: knee property"
short-title: knee
slug: Web/API/DynamicsCompressorNode/knee
page-type: web-api-instance-property
browser-compat: api.DynamicsCompressorNode.knee
---

{{ APIRef("Web Audio API") }}

ویژگی `knee` در رابط {{ domxref("DynamicsCompressorNode") }} یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که مقداری بر حسب دسیبل را در بر می‌گیرد؛ این مقدار نشان‌دهنده محدوده‌ای بالاتر از آستانه است که در آن منحنی به نرمی به بخش فشرده‌شده گذر می‌کند.

مقدار پیش‌فرض ویژگی `knee` برابر با `30` است و می‌توان آن را بین `0` و `40` تنظیم کرد.

![اثر knee را توصیف می‌کند و دو منحنی را نشان می‌دهد: یکی برای knee سخت و دیگری برای knee نرم.](webaudioknee.png)

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه {{domxref("AudioParam")}} بازگردانده‌شده فقط‌خواندنی است، مقداری که نشان می‌دهد چنین نیست.

## مثال‌ها

```js
const audioCtx = new AudioContext();
const compressor = audioCtx.createDynamicsCompressor();
compressor.knee.value = 40;
```

برای مثال کامل‌تر، به [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)