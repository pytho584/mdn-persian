---
title: "ConvolverNode: normalize property"
short-title: normalize
slug: Web/API/ConvolverNode/normalize
page-type: web-api-instance-property
browser-compat: api.ConvolverNode.normalize
---

{{ APIRef("Web Audio API") }}

ویژگی `normalize` در رابط {{ domxref("ConvolverNode") }} یک مقدار بولین است که مشخص می‌کند آیا هنگام تنظیم ویژگی `buffer`، پاسخ ضربه (impulse response) موجود در بافر با نرمال‌سازی توان برابر (equal-power normalization) مقیاس‌بندی شود یا نه.

مقدار پیش‌فرض آن `true` است تا وقتی کانولور با پاسخ‌های ضربه متنوع بارگذاری می‌شود، سطح خروجی یکنواخت‌تری به دست آید. اگر `normalize` روی `false` تنظیم شود، کانولوشن بدون پیش‌پردازش یا مقیاس‌بندی پاسخ ضربه رندر خواهد شد. تغییرات این مقدار تا دفعه بعدی که ویژگی `buffer` تنظیم شود، اعمال نمی‌شوند.

## مقدار

یک بولین.

## مثال‌ها

### خاموش کردن نرمال‌سازی

مثال زیر یک گره کانولور می‌سازد و یک {{domxref("AudioBuffer")}} به آن اختصاص می‌دهد. قبل از انتصاب بافر صوتی، مقدار `normalize` را روی `false` تنظیم می‌کند.

```js
const audioCtx = new AudioContext();
// …

const convolver = audioCtx.createConvolver();
// …

// Grab audio track via fetch() for convolver node
try {
  const response = await fetch(
    "https://mdn.github.io/voice-change-o-matic/audio/concert-crowd.ogg",
  );
  const arrayBuffer = await response.arrayBuffer();
  const decodedAudio = await audioCtx.decodeAudioData(arrayBuffer);
  convolver.normalize = false; // must be set before the buffer, to take effect
  convolver.buffer = decodedAudio;
} catch (error) {
  console.error(
    `Unable to fetch the audio file: ${name} Error: ${err.message}`,
  );
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)