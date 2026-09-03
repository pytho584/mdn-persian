---
title: "OfflineAudioContext: startRendering() method"
short-title: startRendering()
slug: Web/API/OfflineAudioContext/startRendering
page-type: web-api-instance-method
browser-compat: api.OfflineAudioContext.startRendering
---

{{ APIRef("Web Audio API") }}

متد `startRendering()` در رابط {{ domxref("OfflineAudioContext") }}، رندر کردن گراف صوتی را با در نظر گرفتن اتصالات فعلی و تغییرات زمان‌بندی‌شدهٔ جاری آغاز می‌کند.

هنگامی که فرایند رندر به پایان برسد، رویداد {{domxref("OfflineAudioContext/complete_event", "complete")}} (از نوع {{domxref("OfflineAudioCompletionEvent")}}) صادر می‌شود که شامل {{domxref("AudioBuffer")}} حاصل، در ویژگی `renderedBuffer` خود است.

مرورگرها در حال حاضر از دو نسخهٔ متد `startRendering()` پشتیبانی می‌کنند: نسخهٔ قدیمی‌تر مبتنی بر رویداد و نسخهٔ جدیدتر مبتنی بر وعده (Promise). نسخهٔ اول در نهایت حذف خواهد شد، اما در حال حاضر برای سازگاری با نسخه‌های قبلی، هر دو سازوکار ارائه شده‌اند.

## نحو

```js-nolint
startRendering()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{domxref("AudioBuffer")}} برآورده می‌شود.

## مثال‌ها

### پخش صدا با یک زمینهٔ صوتی آفلاین

در این مثال، یک {{domxref("AudioContext")}} و یک شیء `OfflineAudioContext` تعریف می‌کنیم. از `AudioContext` برای بارگذاری یک قطعهٔ صوتی با {{domxref("Window/fetch", "fetch()")}} استفاده می‌کنیم و سپس از `OfflineAudioContext` برای رندر کردن صدا در یک {{domxref("AudioBufferSourceNode")}} و پخش قطعه از طریق آن بهره می‌بریم. پس از راه‌اندازی گراف صوتی آفلاین، آن را با استفاده از `OfflineAudioContext.startRendering()` به یک {{domxref("AudioBuffer")}} رندر می‌کنیم.

هنگامی که وعدهٔ `startRendering()` برآورده شود، رندر کامل شده و `AudioBuffer` خروجی از آن وعده بازگردانده می‌شود.

در این مرحله، یک زمینهٔ صوتی دیگر می‌سازیم، داخل آن یک {{domxref("AudioBufferSourceNode")}} ایجاد می‌کنیم و بافر آن را برابر با همان `AudioBuffer` وعده قرار می‌دهیم. سپس این گره به‌عنوان بخشی از یک گراف صوتی استاندارد ساده پخش می‌شود.

> [!NOTE]
> می‌توانید [نمونهٔ کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/offline-audio-context-promise/) یا [سورس آن را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/offline-audio-context-promise).

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

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
```