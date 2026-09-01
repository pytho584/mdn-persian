---
title: "DynamicsCompressorNode: reduction property"
short-title: reduction
slug: Web/API/DynamicsCompressorNode/reduction
page-type: web-api-instance-property
browser-compat: api.DynamicsCompressorNode.reduction
---

{{ APIRef("Web Audio API") }}

ویژگی فقط خواندنی **`reduction`** در رابط {{ domxref("DynamicsCompressorNode") }} یک عدد اعشاری (float) است که میزان کاهش بهره‌ای (gain reduction) که در حال حاضر توسط کمپرسور روی سیگنال اعمال می‌شود را نشان می‌دهد.

این ویژگی برای اهداف اندازه‌گیری (metering) در نظر گرفته شده است و مقداری بر حسب دسی‌بل (dB) برمی‌گرداند، یا اگر هیچ سیگنالی به `DynamicsCompressorNode` وارد نشود، `0` (بدون کاهش بهره) را برمی‌گرداند. محدوده این مقدار بین `20-` و `0` (بر حسب dB) است.

## Value

یک عدد اعشاری (float).

## Examples

```js
const audioCtx = new AudioContext();
const compressor = audioCtx.createDynamicsCompressor();
const myReduction = compressor.reduction;
```

برای کد مثال کامل‌تر به [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)