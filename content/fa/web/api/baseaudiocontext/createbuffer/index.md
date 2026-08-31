---
title: "BaseAudioContext: createBuffer() method"
short-title: createBuffer()
slug: Web/API/BaseAudioContext/createBuffer
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createBuffer
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

متد `createBuffer()` از رابط {{ domxref("BaseAudioContext") }} برای ایجاد یک شیء جدید و خالی {{ domxref("AudioBuffer") }} استفاده می‌شود که سپس می‌تواند با داده پر شود و از طریق یک {{ domxref("AudioBufferSourceNode")}} پخش شود.

برای جزئیات بیشتر درباره بافرهای صوتی، به صفحه مرجع {{ domxref("AudioBuffer") }} مراجعه کنید.

> [!NOTE]
> `createBuffer()` قبلاً می‌توانست داده‌های فشرده را بگیرد و نمونه‌های رمزگشایی شده را برگرداند، اما این قابلیت از مشخصات حذف شد، زیرا تمام رمزگشایی در رشته اصلی انجام می‌شد، بنابراین `createBuffer()` اجرای کدهای دیگر را مسدود می‌کرد. متد ناهمزمان `decodeAudioData()` کار مشابهی انجام می‌دهد — صدای فشرده مانند یک فایل MP3 را می‌گیرد و مستقیماً یک {{ domxref("AudioBuffer") }} به شما برمی‌گرداند که سپس می‌توانید از طریق یک {{ domxref("AudioBufferSourceNode") }} پخش کنید. برای موارد استفاده ساده مانند پخش MP3، باید از `decodeAudioData()` استفاده کنید.

برای توضیح عمیق درباره نحوه کار بافرهای صوتی، از جمله نحوه عملکرد پارامترها، [بافرهای صوتی: فریم‌ها، نمونه‌ها و کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_buffers_frames_samples_and_channels) را از راهنمای مفاهیم پایه ما بخوانید.

## Syntax

```js-nolint
createBuffer(numOfChannels, length, sampleRate)
```

### Parameters

- `numOfChannels`
  - : یک عدد صحیح که تعداد کانال‌هایی که این بافر باید داشته باشد را نشان می‌دهد. مقدار پیش‌فرض 1 است و همه عامل‌های کاربر باید حداقل 32 کانال را پشتیبانی کنند.
- `length`
  - : یک عدد صحیح که اندازه بافر را بر حسب نمونه-فریم نشان می‌دهد (که در آن هر نمونه-فریم اندازه یک نمونه بر حسب بایت ضرب در `numOfChannels` است). برای تعیین `length` برای تعداد ثانیه مشخصی از صدا، از `numSeconds * sampleRate` استفاده کنید.
- `sampleRate`
  - : نرخ نمونه‌برداری داده‌های صوتی خطی بر حسب نمونه-فریم در ثانیه. همه مرورگرها باید حداقل از نرخ‌های نمونه‌برداری در محدوده 8000 هرتز تا 96000 هرتز پشتیبانی کنند.

### Return value

یک {{domxref("AudioBuffer")}} که بر اساس گزینه‌های مشخص شده پیکربندی شده است.

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر یک یا چند گزینه منفی باشند یا مقدار نامعتبر داشته باشند (مانند `numberOfChannels` بیشتر از حد پشتیبانی شده، یا `sampleRate` خارج از محدوده اسمی) پرتاب می‌شود.
- {{jsxref("RangeError")}}
  - : اگر حافظه کافی برای تخصیص بافر در دسترس نباشد پرتاب می‌شود.

## Examples

ابتدا چند مثال ساده و پیش‌پا افتاده برای کمک به توضیح نحوه استفاده از پارامترها:

```js
const audioCtx = new AudioContext();
const buffer = audioCtx.createBuffer(2, 22050, 44100);
```

اگر از این فراخوانی استفاده کنید، یک بافر استریو (دو کانال) دریافت می‌کنید که وقتی روی یک AudioContext با نرخ 44100Hz (بسیار رایج، اکثر کارت‌های صوتی معمولی با این نرخ کار می‌کنند) پخش شود، برای 0.5 ثانیه طول می‌کشد: 22050 فریم / 44100Hz = 0.5 ثانیه.

```js
const audioCtx = new AudioContext();
const buffer = audioCtx.createBuffer(1, 22050, 22050);
```

اگر از این فراخوانی استفاده کنید، یک بافر مونو (یک کانال) دریافت می‌کنید که وقتی روی یک `AudioContext` با نرخ 44100Hz پخش شود، به طور خودکار به 44100Hz _نمونه‌برداری مجدد_ می‌شود (و بنابراین 44100 فریم تولید می‌کند) و برای 1.0 ثانیه طول می‌کشد: 44100 فریم / 44100Hz = 1 ثانیه.

> [!NOTE]
> نمونه‌برداری مجدد صدا بسیار شبیه به تغییر اندازه تصویر است: فرض کنید یک تصویر 16x16 دارید، اما می‌خواهید یک ناحیه 32x32 را پر کند: آن را تغییر اندازه (نمونه‌برداری مجدد) می‌دهید. نتیجه کیفیت کمتری دارد (بسته به الگوریتم تغییر اندازه می‌تواند تار یا دندانه‌دار باشد)، اما کار می‌کند و تصویر تغییر اندازه داده شده فضای کمتری اشغال می‌کند. صدای نمونه‌برداری مجدد دقیقاً همین است — شما فضا ذخیره می‌کنید، اما در عمل نمی‌توانید محتوای فرکانس بالا (صدای زیر) را به درستی بازتولید کنید.

حالا بیایید به یک مثال پیچیده‌تر از `createBuffer()` نگاه کنیم، که در آن یک بافر سه ثانیه‌ای ایجاد می‌کنیم، آن را با نویز سفید پر می‌کنیم و سپس از طریق یک {{domxref("AudioBufferSourceNode")}} پخش می‌کنیم. کامنت‌ها باید به وضوح توضیح دهند که چه اتفاقی می‌افتد. همچنین می‌توانید [کد را به صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer/) یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/blob/main/audio-buffer/index.html).

```js
const audioCtx = new AudioContext();

// Create an empty three-second stereo buffer at the sample rate of the AudioContext
const myArrayBuffer = audioCtx.createBuffer(
  2,
  audioCtx.sampleRate * 3,
  audioCtx.sampleRate,
);

// Fill the buffer with white noise;
// just random values between -1.0 and 1.0
for (let channel = 0; channel < myArrayBuffer.numberOfChannels; channel++) {
  // This gives us the actual ArrayBuffer that contains the data
  const nowBuffering = myArrayBuffer.getChannelData(channel);
  for (let i = 0; i < myArrayBuffer.length; i++) {
    // Math.random() is in [0; 1.0]
    // audio needs to be in [-1.0; 1.0]
    nowBuffering[i] = Math.random() * 2 - 1;
  }
}

// Get an AudioBufferSourceNode.
// This is the AudioNode to use when we want to play an AudioBuffer
const source = audioCtx.createBufferSource();
// set the buffer in the AudioBufferSourceNode
source.buffer = myArrayBuffer;
// connect the AudioBufferSourceNode to the
// destination so we can hear the sound
source.connect(audioCtx.destination);
// start the source playing
source.start();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)