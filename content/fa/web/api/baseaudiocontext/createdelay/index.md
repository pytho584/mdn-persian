---
title: "BaseAudioContext: createDelay() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createDelay"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createDelay() method"
short-title: createDelay()
slug: Web/API/BaseAudioContext/createDelay
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createDelay
---

{{APIRef("Web Audio API")}}

متد `createDelay()` از رابط {{domxref("BaseAudioContext")}} برای ایجاد یک {{domxref("DelayNode")}} استفاده می‌شود که برای تأخیر انداختن سیگنال صوتی ورودی به میزان مشخصی از زمان به کار می‌رود.

> [!NOTE]
> سازنده {{domxref("DelayNode.DelayNode", "DelayNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("DelayNode")}} است؛ برای اطلاعات بیشتر به
> [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## Syntax

```js-nolint
createDelay(maxDelayTime)
```

### Parameters

- `maxDelayTime` {{optional_inline}}
  - : حداکثر مقدار زمان (بر حسب ثانیه) که سیگنال صوتی می‌تواند تأخیر داشته باشد. این مقدار باید کمتر از ۱۸۰ ثانیه باشد و در صورت عدم تعیین، مقدار پیش‌فرض ۱ ثانیه است.

### Return value

یک {{domxref("DelayNode")}}. مقدار پیش‌فرض {{domxref("DelayNode.delayTime")}} صفر ثانیه است.

## Examples

ما یک مثال ساخته‌ایم که به شما امکان می‌دهد سه نمونه مختلف را در یک حلقه ثابت پخش کنید — به [create-delay](https://chrisdavidmills.github.io/create-delay/) مراجعه کنید (همچنین می‌توانید
[کد منبع](https://github.com/chrisdavidmills/create-delay) را مشاهده کنید). اگر
فقط دکمه‌های پخش را فشار دهید، حلقه‌ها بلافاصله شروع می‌شوند؛ اگر نوار لغزنده را به سمت راست بکشید و سپس دکمه‌های پخش را فشار دهید، یک تأخیر اعمال می‌شود، به طوری که صداهای حلقه‌شونده برای مدت کوتاهی شروع به پخش نمی‌کنند.

```js
const audioCtx = new AudioContext();

const synthDelay = audioCtx.createDelay(5.0);

// …

let synthSource;

playSynth.onclick = () => {
  synthSource = audioCtx.createBufferSource();
  synthSource.buffer = buffers[2];
  synthSource.loop = true;
  synthSource.start();
  synthSource.connect(synthDelay);
  synthDelay.connect(destination);
  this.setAttribute("disabled", "disabled");
};

stopSynth.onclick = () => {
  synthSource.disconnect(synthDelay);
  synthDelay.disconnect(destination);
  synthSource.stop();
  playSynth.removeAttribute("disabled");
};

// …

let delay1;
rangeSynth.oninput = () => {
  delay1 = rangeSynth.value;
  synthDelay.delayTime.setValueAtTime(delay1, audioCtx.currentTime);
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)