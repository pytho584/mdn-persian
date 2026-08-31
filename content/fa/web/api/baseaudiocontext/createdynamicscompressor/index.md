---
title: "BaseAudioContext: createDynamicsCompressor() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createDynamicsCompressor() method"
short-title: createDynamicsCompressor()
slug: Web/API/BaseAudioContext/createDynamicsCompressor
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createDynamicsCompressor
---

{{ APIRef("Web Audio API") }}

متد `createDynamicsCompressor()` از رابط {{domxref("BaseAudioContext")}} برای ایجاد یک {{domxref("DynamicsCompressorNode")}} استفاده می‌شود که می‌توان از آن برای اعمال فشرده‌سازی بر روی سیگنال صوتی استفاده کرد.

فشرده‌سازی بلندی بلندترین بخش‌های سیگنال را کاهش می‌دهد و بلندی بخش‌های کم‌صدا را افزایش می‌دهد. به‌طور کلی، می‌توان صدای بلندتر، غنی‌تر و پربارتری به دست آورد. این امر به‌ویژه در بازی‌ها و برنامه‌های موسیقی که تعداد زیادی صداهای مجزا به‌طور هم‌زمان پخش می‌شوند، مهم است؛ جایی که می‌خواهید سطح کلی سیگنال را کنترل کنید و به جلوگیری از کلیپینگ (اعوجاج) خروجی صوتی کمک کنید.

> [!NOTE]
> سازندهٔ {{domxref("DynamicsCompressorNode.DynamicsCompressorNode", "DynamicsCompressorNode()")}}
> روش پیشنهادی برای ایجاد یک {{domxref("DynamicsCompressorNode")}} است؛ به
> [Creating an AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## نحو

```js-nolint
createDynamicsCompressor()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{domxref("DynamicsCompressorNode")}}.

## مثال‌ها

کد زیر نحوهٔ استفاده از `createDynamicsCompressor()` را برای افزودن فشرده‌سازی به یک قطعهٔ صوتی نشان می‌دهد. برای مثالی کامل‌تر، به [basic Compressor example](https://mdn.github.io/webaudio-examples/compressor-example/) ([view the source code](https://github.com/mdn/webaudio-examples/tree/main/compressor-example)) نگاهی بیندازید.

```js
// Create a MediaElementAudioSourceNode
// Feed the HTMLMediaElement into it
const source = audioCtx.createMediaElementSource(myAudio);

// Create a compressor node
const compressor = audioCtx.createDynamicsCompressor();
compressor.threshold.setValueAtTime(-50, audioCtx.currentTime);
compressor.knee.setValueAtTime(40, audioCtx.currentTime);
compressor.ratio.setValueAtTime(12, audioCtx.currentTime);
compressor.attack.setValueAtTime(0, audioCtx.currentTime);
compressor.release.setValueAtTime(0.25, audioCtx.currentTime);

// connect the AudioBufferSourceNode to the destination
source.connect(audioCtx.destination);

button.onclick = () => {
  const active = button.getAttribute("data-active");
  if (active === "false") {
    button.setAttribute("data-active", "true");
    button.textContent = "Remove compression";

    source.disconnect(audioCtx.destination);
    source.connect(compressor);
    compressor.connect(audioCtx.destination);
  } else if (active === "true") {
    button.setAttribute("data-active", "false");
    button.textContent = "Add compression";

    source.disconnect(compressor);
    compressor.disconnect(audioCtx.destination);
    source.connect(audioCtx.destination);
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)