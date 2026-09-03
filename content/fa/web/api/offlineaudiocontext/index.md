---
title: OfflineAudioContext
slug: Web/API/OfflineAudioContext
page-type: web-api-interface
browser-compat: api.OfflineAudioContext
---

{{APIRef("Web Audio API")}}

رابط `OfflineAudioContext` یک رابط {{domxref("AudioContext")}} است که یک گراف پردازش صوتی ساخته‌شده از گره‌های صوتی ({{domxref("AudioNode")}}) متصل‌به‌هم را نمایش می‌دهد. برخلاف یک {{domxref("AudioContext")}} استاندارد، یک `OfflineAudioContext` صدا را به سخت‌افزار دستگاه خروجی نمی‌دهد؛ در عوض، آن را با سریع‌ترین سرعت ممکن تولید می‌کند و نتیجه را در یک {{domxref("AudioBuffer")}} قرار می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("OfflineAudioContext.OfflineAudioContext()", "OfflineAudioContext()")}}
  - : یک نمونه جدید از `OfflineAudioContext` می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، یعنی {{domxref("BaseAudioContext")}} را به ارث می‌برد._

- {{domxref('OfflineAudioContext.length')}} {{ReadOnlyInline}}
  - : یک عدد صحیح که اندازه بافر را بر حسب فریم‌های نمونه (sample-frames) نشان می‌دهد.

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، یعنی {{domxref("BaseAudioContext")}} را به ارث می‌برد._

- {{domxref("OfflineAudioContext.suspend()")}}
  - : تعلیق پیشروی زمان در زمینه صوتی را در زمان مشخص‌شده زمان‌بندی می‌کند و یک promise برمی‌گرداند.
- {{domxref("OfflineAudioContext.startRendering()")}}
  - : رندر صدا را با در نظر گرفتن اتصالات فعلی و تغییرات زمان‌بندی‌شده فعلی آغاز می‌کند. این صفحه هم نسخه مبتنی بر رویداد و هم نسخه مبتنی بر promise را پوشش می‌دهد.

### روش‌های منسوخ‌شده

- {{domxref("OfflineAudioContext.resume()")}}
  - : پیشروی زمان را در یک زمینه صوتی که قبلاً معلق شده است، از سر می‌گیرد.

> [!NOTE]
> روش `resume()` همچنان در دسترس است — اکنون در رابط {{domxref("BaseAudioContext")}} تعریف شده است (به {{domxref("AudioContext.resume")}} مراجعه کنید) و بنابراین از طریق هر دو رابط {{domxref("AudioContext")}} و `OfflineAudioContext` قابل دسترسی است.

## رویدادها

به این رویدادها با استفاده از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید:

- [`complete`](/en-US/docs/Web/API/OfflineAudioContext/complete_event)
  - : زمانی فعال می‌شود که رندر یک زمینه صوتی آفلاین کامل شود.

## مثال‌ها

### پخش صدا با یک زمینه صوتی آفلاین

در این مثال، ما هم یک {{domxref("AudioContext")}} و هم یک شیء `OfflineAudioContext` تعریف می‌کنیم. از `AudioContext` برای بارگذاری یک قطعه صوتی با {{domxref("Window/fetch", "fetch()")}} استفاده می‌کنیم و سپس از `OfflineAudioContext` برای رندر کردن صدا در یک {{domxref("AudioBufferSourceNode")}} و پخش قطعه استفاده می‌کنیم. پس از تنظیم گراف صوتی آفلاین، آن را با استفاده از `OfflineAudioContext.startRendering()` در یک {{domxref("AudioBuffer")}} رندر می‌کنیم.

وقتی promise مربوط به `startRendering()` با موفقیت انجام شود، رندر کامل شده و `AudioBuffer` خروجی از داخل promise بازگردانده می‌شود.

در این مرحله، یک زمینه صوتی دیگر می‌سازیم، یک {{domxref("AudioBufferSourceNode")}} در داخل آن ایجاد می‌کنیم و بافر آن را برابر با `AudioBuffer` حاصل از promise قرار می‌دهیم. سپس این به عنوان بخشی از یک گراف صوتی استاندارد ساده پخش می‌شود.

> [!NOTE]
> می‌توانید [نمونه کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/offline-audio-context-promise/)، یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/offline-audio-context-promise).

```js
// Define both online and offline audio contexts
let audioCtx; // Must be initialized after a user interaction
const offlineCtx = new OfflineAudioContext(2, 44100 * 40, 44100);

// Define constants for dom nodes
const play = document.querySelector("#play");

function getData() {
  // Fetch an audio track, decode it and stick it in a buffer.
  // Then we put the buffer into the source and can play it.
  fetch("viper.ogg")
    .then((response) => response.arrayBuffer())
    .then((downloadedBuffer) => audioCtx.decodeAudioData(downloadedBuffer))
    .then((decodedBuffer) => {
      console.log("File downloaded successfully.");
      const source = new AudioBufferSourceNode(offlineCtx, {
        buffer: decodedBuffer,
      });
      source.connect(offlineCtx.destination);
      return source.start();
    })
    .then(() => offlineCtx.startRendering())
    .then((renderedBuffer) => {
      console.log("Rendering completed successfully.");
      play.disabled = false;
      const song = new AudioBufferSourceNode(audioCtx, {
        buffer: renderedBuffer,
      });
      song.connect(audioCtx.destination);

      // Start the song
      song.start();
    })
    .catch((err) => {
      console.error(`Error encountered: ${err}`);
    });
}

// Activate the play button
play.onclick = () => {
  play.disabled = true;
  // We can initialize the context as the user clicked.
  audioCtx = new AudioContext();

  // Fetch the data and start the song
  getData();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)