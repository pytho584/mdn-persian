---
title: "ConvolverNode: buffer property"
---

---
title: "ConvolverNode: buffer property"
short-title: buffer
slug: Web/API/ConvolverNode/buffer
page-type: web-api-instance-property
browser-compat: api.ConvolverNode.buffer
---

{{ APIRef("Web Audio API") }}

ویژگی **`buffer`** در رابط {{ domxref("ConvolverNode") }} یک {{domxref("AudioBuffer")}} مونو، استریو یا چهارکاناله را نشان می‌دهد که حاوی پاسخ ضربه (impulse response) (احتمالاً چندکاناله) است و توسط `ConvolverNode` برای ایجاد افکت طنین (reverb) استفاده می‌شود.

این معمولاً یک ضبط ساده از نزدیک‌ترین چیز به یک ضربه است که می‌توان در فضای مورد نظر برای مدل‌سازی یافت. برای مثال، اگر بخواهید طنین حمام خانه خود را مدل‌سازی کنید، می‌توانید یک میکروفون نزدیک درب قرار دهید و صدای ترکیدن بادکنک یا یک ضربهٔ مصنوعی تولیدشده از سینک را ضبط کنید. آن ضبط صوتی سپس می‌تواند به‌عنوان بافر استفاده شود.

این بافر صوتی باید نرخ نمونه‌برداری (sample-rate) یکسانی با `AudioContext` داشته باشد؛ در غیر این صورت یک استثنا پرتاب خواهد شد. در زمانی که این ویژگی تنظیم می‌شود، بافر و وضعیت ویژگی برای پیکربندی `ConvolverNode` با این پاسخ ضربه و با نرمال‌سازی مشخص‌شده استفاده خواهند شد. مقدار اولیهٔ این ویژگی `null` است.

## مقدار

یک {{domxref("AudioBuffer")}}.

## مثال‌ها

### اختصاص یک بافر صوتی

مثال زیر یک گره کانوالور (convolver node) ایجاد می‌کند و یک {{domxref("AudioBuffer")}} به آن اختصاص می‌دهد.

برای مثال‌ها/اطلاعات کاربردی کامل‌تر، به دموی [Voice-change-O-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) مراجعه کنید (برای کدی که در ادامه آورده شده، [app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js) را ببینید).

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

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)