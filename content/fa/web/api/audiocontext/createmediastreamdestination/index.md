---
title: "AudioContext: createMediaStreamDestination() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/createMediaStreamDestination"
translated_by: "n8n + AI"
---

---
title: "AudioContext: createMediaStreamDestination() method"
short-title: createMediaStreamDestination()
slug: Web/API/AudioContext/createMediaStreamDestination
page-type: web-api-instance-method
browser-compat: api.AudioContext.createMediaStreamDestination
---

{{ APIRef("Web Audio API") }}

متد `createMediaStreamDestination()` از رابط {{ domxref("AudioContext") }} برای ایجاد یک شیء جدید {{domxref("MediaStreamAudioDestinationNode")}} استفاده می‌شود که با یک {{domxref("MediaStream")}} از نوع [WebRTC](/en-US/docs/Web/API/WebRTC_API) مرتبط است. این `MediaStream` یک جریان صوتی را نمایش می‌دهد که می‌تواند در یک فایل محلی ذخیره شود یا به کامپیوتر دیگری ارسال گردد.

{{domxref("MediaStream")}} در زمان ایجاد گره ساخته می‌شود و از طریق ویژگی `stream` متعلق به {{domxref("MediaStreamAudioDestinationNode")}} قابل دسترسی است. این جریان را می‌توان به همان شیوه‌ای که یک `MediaStream` به دست آمده از طریق {{domxref("navigator.getUserMedia") }} استفاده می‌شود، به کار برد — برای مثال، می‌توان آن را با استفاده از متد `addStream()` مربوط به `RTCPeerConnection` به یک همتای راه دور ارسال کرد.

برای جزئیات بیشتر درباره گره‌های مقصد جریان رسانه، به صفحه مرجع {{domxref("MediaStreamAudioDestinationNode")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
createMediaStreamDestination()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("MediaStreamAudioDestinationNode")}}.

## مثال‌ها

در مثال ساده زیر، یک {{domxref("MediaStreamAudioDestinationNode")}}، یک {{ domxref("OscillatorNode") }} و یک {{ domxref("MediaRecorder") }} ایجاد می‌کنیم (بنابراین این مثال در حال حاضر فقط در Firefox و Chrome کار خواهد کرد). `MediaRecorder` برای ضبط اطلاعات از `MediaStreamDestinationNode` تنظیم شده است.

وقتی دکمه کلیک می‌شود، اسیلاتور شروع به کار می‌کند و `MediaRecorder` شروع به ضبط می‌کند. وقتی دکمه متوقف می‌شود، اسیلاتور و `MediaRecorder` هر دو متوقف می‌شوند. توقف `MediaRecorder` باعث می‌شود رویداد `dataavailable` رخ دهد و داده‌های رویداد به آرایه `chunks` اضافه شوند. پس از آن، رویداد `stop` رخ می‌دهد، یک `blob` جدید از نوع opus ساخته می‌شود — که داده‌های موجود در آرایه `chunks` را شامل می‌شود — و یک پنجره (تب) جدید باز می‌شود که به آدرسی ساخته شده از آن blob اشاره می‌کند.

از اینجا می‌توانید فایل opus را پخش و ذخیره کنید.

```html
<button>Make sine wave</button> <audio controls></audio>
```

```js
const b = document.querySelector("button");
let clicked = false;
const chunks = [];
const ac = new AudioContext();
const osc = ac.createOscillator();
const dest = ac.createMediaStreamDestination();
const mediaRecorder = new MediaRecorder(dest.stream);
osc.connect(dest);

b.addEventListener("click", (e) => {
  if (!clicked) {
    mediaRecorder.start();
    osc.start(0);
    e.target.textContent = "Stop recording";
    clicked = true;
  } else {
    mediaRecorder.stop();
    osc.stop(0);
    e.target.disabled = true;
  }
});

mediaRecorder.ondataavailable = (evt) => {
  // Push each chunk (blobs) in an array
  chunks.push(evt.data);
};

mediaRecorder.onstop = (evt) => {
  // Make blob out of our blobs, and open it.
  const blob = new Blob(chunks, { type: "audio/ogg; codecs=opus" });
  document.querySelector("audio").src = URL.createObjectURL(blob);
};
```

> [!NOTE]
> می‌توانید [این مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/webaudio-examples/create-media-stream-destination/index.html)، یا [کد منبع آن را مطالعه کنید](https://github.com/mdn/webaudio-examples/blob/main/create-media-stream-destination/index.html) در GitHub.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)