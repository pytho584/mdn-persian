---
title: "MediaRecorder: resume event"
short-title: resume
slug: Web/API/MediaRecorder/resume_event
page-type: web-api-event
browser-compat: api.MediaRecorder.resume_event
---

{{APIRef("MediaStream Recording")}}

رویداد **`resume`** از رابط {{domxref("MediaRecorder")}} زمانی فعال می‌شود که متد {{domxref("MediaRecorder.resume()")}} فراخوانی گردد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("resume", (event) => { })

onresume = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

```js
pause.onclick = () => {
  if (MediaRecorder.state === "recording") {
    mediaRecorder.pause();
    // recording paused
  } else if (MediaRecorder.state === "paused") {
    mediaRecorder.resume();
    // resume recording
  }
};

mediaRecorder.onpause = () => {
  // do something in response to
  // recording being paused
};

mediaRecorder.onresume = () => {
  // do something in response to
  // recording being resumed
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): نمایشی از MediaRecorder + getUserMedia + تجسم Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [نمایش ضبط MediaStream از simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia")}}