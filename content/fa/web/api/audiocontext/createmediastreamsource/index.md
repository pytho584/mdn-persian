---
title: "AudioContext: createMediaStreamSource() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/createMediaStreamSource"
short-title: createMediaStreamSource()
slug: Web/API/AudioContext/createMediaStreamSource
page-type: web-api-instance-method
browser-compat: api.AudioContext.createMediaStreamSource
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

متد `createMediaStreamSource()` از رابط {{ domxref("AudioContext") }} برای ایجاد یک شیء جدید {{ domxref("MediaStreamAudioSourceNode") }} استفاده می‌شود، که یک جریان رسانه‌ای (مثلاً از یک نمونه {{ domxref("MediaDevices.getUserMedia") }}) داده می‌شود و صدای آن می‌تواند پخش و دستکاری شود.

برای جزئیات بیشتر درباره گره‌های منبع صوتی جریان رسانه‌ای، صفحه مرجع {{domxref("MediaStreamAudioSourceNode")}} را بررسی کنید.

## Syntax

```js-nolint
createMediaStreamSource(stream)
```

### Parameters

- `stream`
  - : یک {{domxref("MediaStream")}} که به عنوان یک منبع صوتی برای تغذیه به یک گراف پردازش صوتی برای استفاده و دستکاری استفاده می‌شود.

### Return value

یک شیء جدید {{domxref("MediaStreamAudioSourceNode")}} که نمایانگر گره صوتی است که رسانه آن از جریان منبع مشخص شده به دست آمده است.

## Examples

در این مثال، ما یک جریان رسانه‌ای (صدا + ویدیو) را از {{domxref("navigator.getUserMedia")}} دریافت می‌کنیم، آن را در یک عنصر {{htmlelement("video")}} برای پخش قرار می‌دهیم و سپس صدا را بی‌صدا می‌کنیم، اما همچنین صدا را به یک {{domxref("MediaStreamAudioSourceNode")}} وارد می‌کنیم. سپس، این منبع صوتی را به یک {{ domxref("BiquadFilterNode") }} با فیلتر پایین‌گذر (که به عنوان یک تقویت‌کننده باس عمل می‌کند) و سپس به یک {{domxref("AudioDestinationNode") }} وارد می‌کنیم.

لغزنده محدوده زیر عنصر {{ htmlelement("video") }} میزان بهره اعمال شده به فیلتر پایین‌گذر را کنترل می‌کند — با افزایش مقدار لغزنده، صدا باس‌دارتر می‌شود!

> [!NOTE]
> می‌توانید این [مثال را به صورت زنده](https://mdn.github.io/webaudio-examples/stream-source-buffer/) مشاهده کنید، یا [کد منبع](https://github.com/mdn/webaudio-examples/tree/main/stream-source-buffer) را ببینید.

```js
const pre = document.querySelector("pre");
const video = document.querySelector("video");
const myScript = document.querySelector("script");
const range = document.querySelector("input");

// getUserMedia block - grab stream
// put it into a MediaStreamAudioSourceNode
// also output the visuals into a video element

if (navigator.mediaDevices) {
  console.log("getUserMedia supported.");
  navigator.mediaDevices
    .getUserMedia({ audio: true, video: true })
    .then((stream) => {
      video.srcObject = stream;
      video.onloadedmetadata = (e) => {
        video.play();
        video.muted = true;
      };

      // Create a MediaStreamAudioSourceNode
      // Feed the HTMLMediaElement into it
      const audioCtx = new AudioContext();
      const source = audioCtx.createMediaStreamSource(stream);

      // Create a biquad filter
      const biquadFilter = audioCtx.createBiquadFilter();
      biquadFilter.type = "lowshelf";
      biquadFilter.frequency.value = 1000;
      biquadFilter.gain.value = range.value;

      // connect the AudioBufferSourceNode to the gainNode
      // and the gainNode to the destination, so we can play the
      // music and adjust the volume using the mouse cursor
      source.connect(biquadFilter);
      biquadFilter.connect(audioCtx.destination);

      // Get new mouse pointer coordinates when mouse is moved
      // then set new gain value

      range.oninput = () => {
        biquadFilter.gain.value = range.value;
      };
    })
    .catch((err) => {
      console.log(`The following gUM error occurred: ${err}`);
    });
} else {
  console.log("getUserMedia not supported on your browser!");
}

// dump script to pre element

pre.textContent = myScript.textContent;
```

> [!NOTE]
> در نتیجه فراخوانی `createMediaStreamSource()`، پخش صدا از جریان رسانه‌ای به گراف پردازش {{domxref("AudioContext")}} هدایت می‌شود. بنابراین پخش/توقف جریان همچنان می‌تواند از طریق API عنصر رسانه و کنترل‌های پخش انجام شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)