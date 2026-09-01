---
title: "DynamicsCompressorNode: ratio property"
short-title: ratio
slug: Web/API/DynamicsCompressorNode/ratio
page-type: web-api-instance-property
browser-compat: api.DynamicsCompressorNode.ratio
---

{{ APIRef("Web Audio API") }}

ویژگی `ratio` از رابط {{ domxref("DynamicsCompressorNode") }} یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که میزان تغییر (بر حسب دسی‌بل) لازم در ورودی برای یک تغییر ۱ دسی‌بل در خروجی را نشان می‌دهد.

مقدار پیش‌فرض ویژگی `ratio` برابر `12` است و می‌توان آن را بین `1` و `20` تنظیم کرد.

![اثر نسبت‌های مختلف بر سیگنال خروجی را توصیف می‌کند](webaudioratio.png)

## Value

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه {{domxref("AudioParam")}} برگشتی فقط خواندنی است، اما مقدار آن قابل تغییر است.

## Examples

```js
const audioCtx = new AudioContext();
const compressor = audioCtx.createDynamicsCompressor();
compressor.ratio.value = 12;
```

برای مثال کد کامل‌تر، به [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)