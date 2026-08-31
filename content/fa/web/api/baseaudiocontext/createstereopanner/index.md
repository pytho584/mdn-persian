---
title: "BaseAudioContext: createStereoPanner() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createStereoPanner"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createStereoPanner() method"
short-title: createStereoPanner()
slug: Web/API/BaseAudioContext/createStereoPanner
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createStereoPanner
---

{{ APIRef("Web Audio API") }}

متد `createStereoPanner()` از رابط {{ domxref("BaseAudioContext") }} یک {{ domxref("StereoPannerNode") }} ایجاد می‌کند که می‌تواند برای اعمال پانینگ استریو به یک منبع صوتی استفاده شود. این متد یک جریان صوتی ورودی را با استفاده از [یک الگوریتم پانینگ کم‌هزینه](https://webaudio.github.io/web-audio-api/#stereopanner-algorithm) در یک تصویر استریو قرار می‌دهد.

> [!NOTE]
> سازنده {{domxref("StereoPannerNode.StereoPannerNode", "StereoPannerNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("StereoPannerNode")}} است؛ همچنین به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## نحو

```js-nolint
createStereoPanner()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{domxref("StereoPannerNode")}}.

## مثال‌ها

در مثال [StereoPannerNode](https://mdn.github.io/webaudio-examples/stereo-panner-node/) ما ([کد منبع را ببینید](https://github.com/mdn/webaudio-examples/tree/main/stereo-panner-node))، در HTML یک عنصر ساده {{htmlelement("audio")}} به همراه یک لغزنده {{HTMLElement("input")}} برای افزایش و کاهش مقدار پان داریم. در جاوااسکریپت، یک {{domxref("MediaElementAudioSourceNode")}} و یک {{domxref("StereoPannerNode")}} ایجاد می‌کنیم و آن دو را با استفاده از متد `connect()` به یکدیگر متصل می‌کنیم. سپس از یک رویداد `oninput` برای تغییر مقدار پارامتر {{domxref("StereoPannerNode.pan")}} و به‌روزرسانی نمایش مقدار پان هنگام حرکت لغزنده استفاده می‌کنیم.

حرکت لغزنده به چپ و راست در حین پخش موسیقی، صدا را به ترتیب به بلندگوهای چپ و راست خروجی پان می‌کند.

```js
const audioCtx = new AudioContext();
const myAudio = document.querySelector("audio");

const panControl = document.querySelector(".panning-control");
const panValue = document.querySelector(".panning-value");

// Create a MediaElementAudioSourceNode
// Feed the HTMLMediaElement into it
const source = audioCtx.createMediaElementSource(myAudio);

// Create a stereo panner
const panNode = audioCtx.createStereoPanner();

// Event handler function to increase panning to the right and left
// when the slider is moved

panControl.oninput = () => {
  panNode.pan.setValueAtTime(panControl.value, audioCtx.currentTime);
  panValue.textContent = panControl.value;
};

// connect the MediaElementAudioSourceNode to the panNode
// and the panNode to the destination, so we can play the
// music and adjust the panning using the controls
source.connect(panNode);
panNode.connect(audioCtx.destination);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)