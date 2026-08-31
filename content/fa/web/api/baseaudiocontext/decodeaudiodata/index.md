---
title: "BaseAudioContext: decodeAudioData() method"
short-title: decodeAudioData()
slug: Web/API/BaseAudioContext/decodeAudioData
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.decodeAudioData
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

روش `decodeAudioData()` از رابط {{ domxref("BaseAudioContext") }} برای رمزگشایی غیرهمزمان داده‌های فایل صوتی موجود در یک {{jsxref("ArrayBuffer")}} استفاده می‌شود که از {{domxref("Window/fetch", "fetch()")}}، {{domxref("XMLHttpRequest")}} یا {{domxref("FileReader")}} بارگذاری شده است. {{domxref("AudioBuffer")}} رمزگشایی‌شده به نرخ نمونه‌برداری {{domxref("AudioContext")}} بازنمونه‌برداری می‌شود، سپس به یک callback یا promise منتقل می‌شود.

این روش ترجیحی برای ایجاد یک منبع صوتی برای Web Audio API از یک قطعه صوتی است. این روش فقط روی داده‌های کامل فایل کار می‌کند، نه تکه‌های داده‌های فایل صوتی.

این تابع دو روش جایگزین برای بازگرداندن غیرهمزمان داده‌های صوتی یا پیام‌های خطا پیاده‌سازی می‌کند: یک {{jsxref("Promise")}} برمی‌گرداند که با داده‌های صوتی تکمیل می‌شود، و همچنین برای مدیریت موفقیت یا شکست، آرگومان‌های callback را می‌پذیرد. روش اصلی تعامل با این تابع از طریق مقدار بازگشتی Promise است و پارامترهای callback به دلایل سازگاری با نسخه‌های قدیمی ارائه شده‌اند.

## نحو

```js-nolint
// Promise-based syntax returns a Promise:
decodeAudioData(arrayBuffer)

// Callback syntax has no return value:
decodeAudioData(arrayBuffer, successCallback)
decodeAudioData(arrayBuffer, successCallback, errorCallback)
```

### پارامترها

- `arrayBuffer`
  - : یک ArrayBuffer حاوی داده‌های صوتی که باید رمزگشایی شود، معمولاً از {{domxref("Window/fetch", "fetch()")}}، {{domxref("XMLHttpRequest")}} یا {{domxref("FileReader")}} گرفته می‌شود.
- `successCallback` {{optional_inline}}
  - : یک تابع callback که هنگام پایان موفقیت‌آمیز رمزگشایی فراخوانی می‌شود. تنها آرگومان این callback یک {{domxref("AudioBuffer")}} است که _decodedData_ (داده‌های صوتی PCM رمزگشایی‌شده) را نشان می‌دهد. معمولاً می‌خواهید داده‌های رمزگشایی‌شده را در یک {{domxref("AudioBufferSourceNode")}} قرار دهید، جایی که می‌توانید آن را پخش و هر طور که می‌خواهید دستکاری کنید.
- `errorCallback` {{optional_inline}}
  - : یک callback خطای اختیاری که در صورت بروز خطا در هنگام رمزگشایی داده‌های صوتی فراخوانی می‌شود.

### مقدار بازگشتی

یک شیء {{jsxref("Promise") }} که با _decodedData_ تکمیل می‌شود. اگر از سینتکس XHR استفاده می‌کنید، این مقدار بازگشتی را نادیده گرفته و به جای آن از تابع callback استفاده می‌کنید.

## مثال‌ها

در این بخش ابتدا نحو مبتنی بر promise و سپس نحو callback را پوشش می‌دهیم.

### نحو مبتنی بر Promise

در این مثال، `loadAudio()` از {{domxref("Window/fetch", "fetch()")}} برای دریافت یک فایل صوتی استفاده می‌کند و آن را به یک {{domxref("AudioBuffer")}} رمزگشایی می‌کند. سپس `audioBuffer` را در متغیر سراسری `buffer` برای پخش بعدی ذخیره می‌کند.

> [!NOTE]
> می‌توانید [مثال کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/decode-audio-data/promise/)، یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/decode-audio-data/promise).

```js
let audioCtx;
let buffer;
let source;

async function loadAudio() {
  try {
    // Load an audio file
    const response = await fetch("viper.mp3");
    // Decode it
    buffer = await audioCtx.decodeAudioData(await response.arrayBuffer());
  } catch (err) {
    console.error(`Unable to fetch the audio file. Error: ${err.message}`);
  }
}
```

### نحو Callback

در این مثال، `loadAudio()` از {{domxref("Window/fetch", "fetch()")}} برای دریافت یک فایل صوتی استفاده می‌کند و آن را با استفاده از نسخه مبتنی بر callback از `decodeAudioData()` به یک {{domxref("AudioBuffer")}} رمزگشایی می‌کند. در callback، بافر رمزگشایی‌شده را پخش می‌کند.

> [!NOTE]
> می‌توانید [مثال کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/decode-audio-data/callback/)، یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/decode-audio-data/callback).

```js
let audioCtx;
let source;

function playBuffer(buffer) {
  source = audioCtx.createBufferSource();
  source.buffer = buffer;
  source.connect(audioCtx.destination);
  source.loop = true;
  source.start();
}

async function loadAudio() {
  try {
    // Load an audio file
    const response = await fetch("viper.mp3");
    // Decode it
    audioCtx.decodeAudioData(await response.arrayBuffer(), playBuffer);
  } catch (err) {
    console.error(`Unable to fetch the audio file. Error: ${err.message}`);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)