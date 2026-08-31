---
title: "AudioProcessingEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioProcessingEvent"
translated_by: "n8n + AI"
---

---
title: AudioProcessingEvent
slug: Web/API/AudioProcessingEvent
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.AudioProcessingEvent
---

{{APIRef("Web Audio API")}}{{deprecated_header}}

رابطه `AudioProcessingEvent` در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) رویدادهایی را نشان می‌دهد که زمانی رخ می‌دهند که یک بافر ورودی {{domxref("ScriptProcessorNode")}} آماده پردازش است.

یک رویداد `audioprocess` با این رابط روی {{domxref("ScriptProcessorNode")}} زمانی که پردازش صوتی لازم است فعال می‌شود. در طول پردازش صوتی، بافر ورودی خوانده و پردازش می‌شود تا داده‌های صوتی خروجی تولید شود، که سپس در بافر خروجی نوشته می‌شود.

> [!WARNING]
> این ویژگی منسوخ شده است و باید با یک [`AudioWorklet`](/en-US/docs/Web/API/AudioWorklet) جایگزین شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("AudioProcessingEvent.AudioProcessingEvent", "AudioProcessingEvent()")}} {{Deprecated_Inline}}
  - : یک شیء `AudioProcessingEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های به ارث رسیده از والد خود، {{domxref("Event")}}، را پیاده‌سازی می‌کند._

- {{domxref("AudioProcessingEvent.playbackTime", "playbackTime")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : یک عدد اعشاری (double) که زمان پخش صدا را نشان می‌دهد، همانطور که توسط زمان {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} تعریف شده است.
- {{domxref("AudioProcessingEvent.inputBuffer", "inputBuffer")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : یک {{domxref("AudioBuffer")}} که بافر حاوی داده‌های صوتی ورودی برای پردازش است. تعداد کانال‌ها به عنوان پارامتر `numberOfInputChannels` از متد کارخانه‌ای {{domxref("BaseAudioContext/createScriptProcessor", "AudioContext.createScriptProcessor()")}} تعریف می‌شود. توجه داشته باشید که <code>AudioBuffer</code> برگشتی فقط در محدوده کنترل‌کننده رویداد معتبر است.
- {{domxref("AudioProcessingEvent.outputBuffer", "outputBuffer")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : یک {{domxref("AudioBuffer")}} که بافری است که داده‌های صوتی خروجی باید در آن نوشته شود. تعداد کانال‌ها به عنوان پارامتر <code>numberOfOutputChannels</code> از متد کارخانه‌ای {{domxref("BaseAudioContext/createScriptProcessor", "AudioContext.createScriptProcessor()")}} تعریف می‌شود. توجه داشته باشید که <code>AudioBuffer</code> برگشتی فقط در محدوده کنترل‌کننده رویداد معتبر است.

## مثال‌ها

### افزودن نویز سفید با استفاده از یک پردازنده اسکریپت

مثال زیر نحوه استفاده از یک `ScriptProcessorNode` را برای گرفتن یک قطعه صوتی بارگذاری‌شده از طریق {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}}، پردازش آن، افزودن کمی نویز سفید به هر نمونه صوتی از قطعه ورودی (بافر) و پخش آن از طریق {{domxref("AudioDestinationNode")}} نشان می‌دهد. برای هر کانال و هر قاب نمونه، تابع `scriptNode.onaudioprocess` رویداد صوتی مرتبط (`audioProcessingEvent`) را دریافت می‌کند و از آن برای حلقه زدن روی هر کانال از بافر ورودی و هر نمونه در هر کانال استفاده می‌کند و مقدار کمی نویز سفید اضافه می‌کند، سپس نتیجه را به عنوان نمونه خروجی در هر مورد تنظیم می‌کند.

> [!NOTE]
> برای یک مثال کامل در حال اجرا، مخزن گیت‌هاب [script-processor-node](https://mdn.github.io/webaudio-examples/script-processor-node/) ما را ببینید. (همچنین می‌توانید به [کد منبع](https://github.com/mdn/webaudio-examples/tree/main/script-processor-node) دسترسی داشته باشید.)

```js
const myScript = document.querySelector("script");
const myPre = document.querySelector("pre");
const playButton = document.querySelector("button");

// Create AudioContext and buffer source
let audioCtx;

async function init() {
  audioCtx = new AudioContext();
  const source = audioCtx.createBufferSource();

  // Create a ScriptProcessorNode with a bufferSize of 4096 and
  // a single input and output channel
  const scriptNode = audioCtx.createScriptProcessor(4096, 1, 1);

  // Load in an audio track using fetch() and decodeAudioData()
  try {
    const response = await fetch("viper.ogg");
    const arrayBuffer = await response.arrayBuffer();
    source.buffer = await audioCtx.decodeAudioData(arrayBuffer);
  } catch (err) {
    console.error(
      `Unable to fetch the audio file: ${name} Error: ${err.message}`,
    );
  }

  // Give the node a function to process audio events
  scriptNode.addEventListener("audioprocess", (audioProcessingEvent) => {
    // The input buffer is the song we loaded earlier
    let inputBuffer = audioProcessingEvent.inputBuffer;

    // The output buffer contains the samples that will be modified
    // and played
    let outputBuffer = audioProcessingEvent.outputBuffer;

    // Loop through the output channels (in this case there is only one)
    for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
      let inputData = inputBuffer.getChannelData(channel);
      let outputData = outputBuffer.getChannelData(channel);

      // Loop through the 4096 samples
      for (let sample = 0; sample < inputBuffer.length; sample++) {
        // make output equal to the same as the input
        outputData[sample] = inputData[sample];

        // add noise to each output sample
        outputData[sample] += (Math.random() * 2 - 1) * 0.1;
      }
    }
  });

  source.connect(scriptNode);
  scriptNode.connect(audioCtx.destination);
  source.start();

  // When the buffer source stops playing, disconnect everything
  source.addEventListener("ended", () => {
    source.disconnect(scriptNode);
    scriptNode.disconnect(audioCtx.destination);
  });
}

// wire up play button
playButton.addEventListener("click", () => {
  if (!audioCtx) {
    init();
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)