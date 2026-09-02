---
title: "MediaRecorder: stop event"
short-title: stop
slug: Web/API/MediaRecorder/stop_event
page-type: web-api-event
browser-compat: api.MediaRecorder.stop_event
---

{{APIRef("MediaStream Recording")}}

رویداد **`stop`** در رابط {{domxref("MediaRecorder")}} زمانی رخ می‌دهد که {{domxref("MediaRecorder.stop()")}} فراخوانی شود، یا زمانی که جریان رسانه‌ای در حال ضبط پایان یابد. در هر دو حالت، پیش از رویداد `stop`، یک رویداد `dataavailable` رخ می‌دهد که {{domxref("Blob")}} ضبط‌شده تا آن لحظه را برای استفاده در برنامه شما در دسترس قرار می‌دهد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("stop", (event) => { })

onstop = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

```js
mediaRecorder.onstop = (e) => {
  console.log("data available after MediaRecorder.stop() called.");

  const audio = document.createElement("audio");
  audio.controls = true;
  const blob = new Blob(chunks, { type: "audio/ogg; codecs=opus" });
  const audioURL = window.URL.createObjectURL(blob);
  audio.src = audioURL;
  console.log("recorder stopped");
};

mediaRecorder.ondataavailable = (e) => {
  chunks.push(e.data);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): دموی تصویری MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone))
- [دموی ضبط MediaStream از simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton)
- {{domxref("Navigator.getUserMedia")}}