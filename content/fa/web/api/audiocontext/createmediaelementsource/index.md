---
title: "AudioContext: createMediaElementSource() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/createMediaElementSource"
translated_by: "n8n + AI"
---

---
title: "AudioContext: createMediaElementSource() method"
short-title: createMediaElementSource()
slug: Web/API/AudioContext/createMediaElementSource
page-type: web-api-instance-method
browser-compat: api.AudioContext.createMediaElementSource
---

{{ APIRef("Web Audio API") }}

متد `createMediaElementSource()` از رابط {{ domxref("AudioContext") }} برای ایجاد یک شیء {{ domxref("MediaElementAudioSourceNode") }} جدید استفاده می‌شود، با توجه به یک عنصر HTML {{htmlelement("audio")}} یا {{htmlelement("video")}} موجود، که صدای آن می‌تواند پخش و دستکاری شود.

برای جزئیات بیشتر درباره گره‌های منبع صوتی عنصر رسانه، به صفحه مرجع {{ domxref("MediaElementAudioSourceNode") }} مراجعه کنید.

## نحو

```js-nolint
createMediaElementSource(myMediaElement)
```

### پارامترها

- `myMediaElement`
  - : یک شیء {{domxref("HTMLMediaElement")}} که می‌خواهید برای دستکاری به یک گراف پردازش صوتی وارد کنید.

### مقدار بازگشتی

یک {{domxref("MediaElementAudioSourceNode")}}.

## مثال‌ها

این مثال ساده با استفاده از `createMediaElementSource()` یک منبع از عنصر {{htmlelement("audio") }} می‌سازد، سپس صدا را قبل از ارسال به {{ domxref("AudioDestinationNode") }} برای پخش، از یک {{ domxref("GainNode") }} عبور می‌دهد. هنگامی که نشانگر ماوس حرکت می‌کند، تابع `updatePage()` فراخوانی می‌شود که بهره فعلی را به صورت نسبت موقعیت Y ماوس تقسیم بر ارتفاع کل پنجره محاسبه می‌کند. بنابراین می‌توانید با حرکت دادن نشانگر ماوس به بالا و پایین، حجم موسیقی در حال پخش را افزایش و کاهش دهید.

> [!NOTE]
> شما همچنین می‌توانید [این مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/webaudio-examples/media-source-buffer/)، یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/media-source-buffer).

```js
const audioCtx = new AudioContext();
const myAudio = document.querySelector("audio");

// Create a MediaElementAudioSourceNode
// Feed the HTMLMediaElement into it
const source = audioCtx.createMediaElementSource(myAudio);

// Create a gain node
const gainNode = audioCtx.createGain();

// Create variables to store mouse pointer Y coordinate
// and HEIGHT of screen
let curY;
const HEIGHT = window.innerHeight;

// Get new mouse pointer coordinates when mouse is moved
// then set new gain value
document.onmousemove = updatePage;

function updatePage(e) {
  curY = e.pageY;
  gainNode.gain.value = curY / HEIGHT;
}

// Connect the AudioBufferSourceNode to the gainNode
// and the gainNode to the destination, so we can play the
// music and adjust the volume using the mouse cursor
source.connect(gainNode);
gainNode.connect(audioCtx.destination);
```

> [!NOTE]
> در نتیجه فراخوانی `createMediaElementSource()`، پخش صدا از {{domxref("HTMLMediaElement")}} به گراف پردازش AudioContext مسیریابی مجدد می‌شود. بنابراین پخش/توقف رسانه همچنان می‌تواند از طریق API عنصر رسانه و کنترل‌های پخش انجام شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)