---
title: "AudioBufferSourceNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode"
translated_by: "n8n + AI"
---

---
title: AudioBufferSourceNode
slug: Web/API/AudioBufferSourceNode
page-type: web-api-interface
browser-compat: api.AudioBufferSourceNode
---

{{APIRef("Web Audio API")}}

رابط **`AudioBufferSourceNode`** یک {{domxref("AudioScheduledSourceNode")}} است که یک منبع صوتی متشکل از داده‌های صوتی درون حافظه، ذخیره شده در یک {{domxref("AudioBuffer")}}، را نشان می‌دهد.

این رابط به ویژه برای پخش صدایی که نیاز به دقت زمانی بسیار بالایی دارد، مانند صداهایی که باید با یک ریتم خاص مطابقت داشته باشند و می‌توانند در حافظه نگه داشته شوند به جای اینکه از دیسک یا شبکه پخش شوند، مفید است. برای پخش صداهایی که نیاز به زمان‌بندی دقیق دارند اما باید از شبکه پخش شوند یا از دیسک خوانده شوند، از یک {{domxref("AudioWorkletNode")}} برای پیاده‌سازی پخش آن‌ها استفاده کنید.

{{InheritanceDiagram}}

یک `AudioBufferSourceNode` هیچ ورودی ندارد و دقیقاً یک خروجی دارد که تعداد کانال‌های آن برابر با `AudioBuffer` مشخص شده توسط خاصیت {{domxref("AudioBufferSourceNode.buffer", "buffer")}} آن است. اگر بافری تنظیم نشده باشد – یعنی اگر `buffer` برابر با `null` باشد – خروجی شامل یک کانال سکوت است (هر نمونه 0 است).

یک `AudioBufferSourceNode` فقط یک بار می‌تواند پخش شود؛ پس از هر بار فراخوانی {{domxref("AudioBufferSourceNode.start", "start()")}}، اگر بخواهید همان صدا را دوباره پخش کنید، باید یک گره جدید ایجاد کنید. خوشبختانه، ایجاد این گره‌ها بسیار ارزان است و خود `AudioBuffer`ها را می‌توان برای چندین بار پخش صدا استفاده مجدد کرد. در واقع، می‌توانید از این گره‌ها به صورت "شلیک و فراموش کن" استفاده کنید: گره را ایجاد کنید، `start()` را فراخوانی کنید تا صدا شروع به پخش کند، و حتی به خود زحمت نگه داشتن یک مرجع به آن را ندهید. این گره به طور خودکار در زمان مناسب، که تا پس از اتمام پخش صدا نخواهد بود، جمع‌آوری زباله می‌شود.

فراخوانی‌های متعدد به {{domxref("AudioScheduledSourceNode/stop", "stop()")}} مجاز است. آخرین فراخوانی، فراخوانی قبلی را جایگزین می‌کند، اگر `AudioBufferSourceNode` قبلاً به انتهای بافر نرسیده باشد.

![AudioBufferSourceNode محتوای یک AudioBuffer را برمی‌دارد و](webaudioaudiobuffersourcenode.png)

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>0</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال‌ها</th>
      <td>تعریف شده توسط {{domxref("AudioBuffer")}} مرتبط</td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("AudioBufferSourceNode.AudioBufferSourceNode", "AudioBufferSourceNode()")}}
  - : یک شیء `AudioBufferSourceNode` جدید ایجاد و برمی‌گرداند. به عنوان یک جایگزین، می‌توانید از روش کارخانه‌ای {{domxref("BaseAudioContext.createBufferSource()")}} استفاده کنید؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("AudioScheduledSourceNode")}}، به ارث می‌برد._

- {{domxref("AudioBufferSourceNode.buffer")}}
  - : یک {{domxref("AudioBuffer")}} که دارایی صوتی مورد نظر برای پخش را تعریف می‌کند، یا وقتی روی مقدار `null` تنظیم شود، یک کانال سکوت را تعریف می‌کند (که در آن هر نمونه 0.0 است).
- {{domxref("AudioBufferSourceNode.detune")}}
  - : یک {{domxref("AudioParam")}} با [نرخ k](/en-US/docs/Web/API/AudioParam#k-rate) که انحراف (detuning) پخش را بر حسب [سنت](https://en.wikipedia.org/wiki/Cent_%28music%29) نشان می‌دهد. این مقدار با `playbackRate` ترکیب می‌شود تا سرعت پخش صدا تعیین شود. مقدار پیش‌فرض آن `0` است (به معنی عدم انحراف)، و محدوده اسمی آن از -∞ تا ∞ است.
- {{domxref("AudioBufferSourceNode.loop")}}
  - : یک ویژگی بولی که نشان می‌دهد آیا دارایی صوتی باید وقتی به انتهای {{domxref("AudioBuffer")}} رسید، دوباره پخش شود یا خیر. مقدار پیش‌فرض آن `false` است.
- {{domxref("AudioBufferSourceNode.loopStart")}} {{optional_inline}}
  - : یک مقدار اعشاری که زمان، بر حسب ثانیه، را نشان می‌دهد که پخش {{domxref("AudioBuffer")}} باید از آنجا شروع شود وقتی `loop` برابر با `true` است. مقدار پیش‌فرض آن `0` است (به این معنی که در ابتدای هر حلقه، پخش از ابتدای بافر صوتی شروع می‌شود).
- {{domxref("AudioBufferSourceNode.loopEnd")}} {{optional_inline}}
  - : یک عدد اعشاری که زمان، بر حسب ثانیه، را نشان می‌دهد که پخش {{domxref("AudioBuffer")}} در آن متوقف شده و به زمان مشخص شده توسط `loopStart` بازمی‌گردد، اگر `loop` برابر با `true` باشد. مقدار پیش‌فرض `0` است.
- {{domxref("AudioBufferSourceNode.playbackRate")}}
  - : یک {{domxref("AudioParam")}} با [نرخ k](/en-US/docs/Web/API/AudioParam#k-rate) که ضریب سرعت پخش دارایی صوتی را تعریف می‌کند، به طوری که مقدار 1.0 نرخ نمونه‌برداری طبیعی صدا است. از آنجایی که هیچ تصحیح زیروبمی (pitch correction) روی خروجی اعمال نمی‌شود، می‌توان از این برای تغییر زیروبمی نمونه استفاده کرد. این مقدار با `detune` ترکیب می‌شود تا نرخ پخش نهایی تعیین شود.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("AudioScheduledSourceNode")}}، به ارث می‌برد و روش زیر را بازنویسی می‌کند:_

- {{domxref("AudioBufferSourceNode.start", "start()")}}
  - : پخش داده‌های صوتی موجود در بافر را زمان‌بندی می‌کند، یا بلافاصله پخش را آغاز می‌کند. همچنین امکان تنظیم offset شروع و مدت زمان پخش را فراهم می‌کند.

## مثال‌ها

در این مثال، یک بافر دو ثانیه‌ای ایجاد می‌کنیم، آن را با نویز سفید پر می‌کنیم و سپس با استفاده از یک `AudioBufferSourceNode` آن را پخش می‌کنیم. توضیحات باید به وضوح آنچه را که در حال رخ دادن است، روشن کند.

> [!NOTE]
> همچنین می‌توانید [کد را به صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer/) یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/blob/main/audio-buffer/index.html).

```js
const audioCtx = new AudioContext();

// ایجاد یک بافر استریوی سه ثانیه‌ای خالی با نرخ نمونه‌برداری AudioContext
const myArrayBuffer = audioCtx.createBuffer(
  2,
  audioCtx.sampleRate * 3,
  audioCtx.sampleRate,
);

// پر کردن بافر با نویز سفید؛
// فقط مقادیر تصادفی بین 1.0- و 1.0
for (let channel = 0; channel < myArrayBuffer.numberOfChannels; channel++) {
  // این به ما ArrayBuffer واقعی حاوی داده‌ها را می‌دهد
  const nowBuffering = myArrayBuffer.getChannelData(channel);
  for (let i = 0; i < myArrayBuffer.length; i++) {
    // Math.random() در بازه [0; 1.0] است
    // صدا باید در بازه [-1.0; 1.0] باشد
    nowBuffering[i] = Math.random() * 2 - 1;
  }
}

// دریافت یک AudioBufferSourceNode.
// این AudioNode است که وقتی می‌خواهیم یک AudioBuffer را پخش کنیم از آن استفاده می‌کنیم
const source = audioCtx.createBufferSource();
// تنظیم بافر در AudioBufferSourceNode
source.buffer = myArrayBuffer;
// اتصال AudioBufferSourceNode به
// خروجی نهایی تا بتوانیم صدا را بشنویم
source.connect(audioCtx.destination);
// شروع پخش منبع
source.start();
```

> [!NOTE]
> برای یک مثال `decodeAudioData()`، به صفحه {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)