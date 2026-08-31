---
title: "BaseAudioContext: createScriptProcessor() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createScriptProcessor"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createScriptProcessor() method"
short-title: createScriptProcessor()
slug: Web/API/BaseAudioContext/createScriptProcessor
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.BaseAudioContext.createScriptProcessor
---

{{APIRef("Web Audio API")}}{{deprecated_header}}

متد `createScriptProcessor()` از رابط {{domxref("BaseAudioContext")}} یک {{domxref("ScriptProcessorNode")}} برای پردازش مستقیم صدا ایجاد می‌کند.

> [!NOTE]
> این قابلیت با [AudioWorklets](/en-US/docs/Web/API/AudioWorklet) و رابط {{domxref("AudioWorkletNode")}} جایگزین شده است.

## نحو

```js-nolint
createScriptProcessor(bufferSize, numberOfInputChannels, numberOfOutputChannels)
```

### پارامترها

- `bufferSize`
  - : اندازه بافر بر حسب واحد نمونه-فریم. اگر مشخص شود، bufferSize باید یکی از مقادیر زیر باشد: 256، 512، 1024، 2048، 4096، 8192، 16384. اگر مقدار داده نشود یا برابر 0 باشد، پیاده‌سازی بهترین اندازه بافر را برای محیط داده‌شده انتخاب می‌کند، که در طول عمر گره، توانی ثابت از 2 خواهد بود.

    این مقدار کنترل می‌کند که رویداد `audioprocess` با چه فرکانسی ارسال شود و در هر بار فراخوانی چند نمونه-فریم باید پردازش شود. مقادیر کمتر برای `bufferSize` منجر به تأخیر کمتر (بهتر) می‌شود. مقادیر بیشتر برای جلوگیری از قطع شدن صدا و خطاهای صوتی ضروری هستند. توصیه می‌شود که این اندازه بافر را مشخص نکنید و به پیاده‌سازی اجازه دهید اندازه بافر مناسبی را برای ایجاد تعادل بین تأخیر و کیفیت صدا انتخاب کند.

- `numberOfInputChannels`
  - : عدد صحیحی که تعداد کانال‌های ورودی این گره را مشخص می‌کند؛ پیش‌فرض ۲ است. مقادیر تا ۳۲ پشتیبانی می‌شوند.

- `numberOfOutputChannels`
  - : عدد صحیحی که تعداد کانال‌های خروجی این گره را مشخص می‌کند؛ پیش‌فرض ۲ است. مقادیر تا ۳۲ پشتیبانی می‌شوند.

> [!WARNING]
> وب‌کیت (نسخه ۳۱) در حال حاضر نیاز دارد که یک
> `bufferSize` معتبر هنگام فراخوانی این متد ارسال شود.

> [!NOTE]
> صفر بودن هر دو `numberOfInputChannels` و
> `numberOfOutputChannels` نامعتبر است.

### مقدار بازگشتی

یک {{domxref("ScriptProcessorNode")}}.

## مثال‌ها

### افزودن نویز سفید با استفاده از پردازنده اسکریپتی

مثال زیر نشان می‌دهد که چگونه از یک `ScriptProcessorNode` برای گرفتن یک قطعه صوتی بارگذاری‌شده از طریق {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}}، پردازش آن، افزودن کمی نویز سفید به هر نمونه صوتی از قطعه ورودی، و پخش آن از طریق {{domxref("AudioDestinationNode")}} استفاده کنیم.

برای هر کانال و هر قاب نمونه، کنترل‌کننده رویداد {{domxref("ScriptProcessorNode.audioprocess_event", "audioprocess")}} گره اسکریپتی از `audioProcessingEvent` مرتبط استفاده می‌کند تا در هر کانال از بافر ورودی و هر نمونه در هر کانال حلقه بزند و مقدار کمی نویز سفید اضافه کند، سپس آن نتیجه را به‌عنوان نمونه خروجی در هر مورد تنظیم کند.

> [!NOTE]
> می‌توانید [مثال کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/script-processor-node/) یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/script-processor-node).

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

    // The output buffer contains the samples that will be modified and played
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