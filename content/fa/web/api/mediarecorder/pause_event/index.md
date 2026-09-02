---
title: "MediaRecorder: pause event"
---

---
title: "MediaRecorder: pause event"
short-title: pause
slug: Web/API/MediaRecorder/pause_event
page-type: web-api-event
browser-compat: api.MediaRecorder.pause_event
---

{{APIRef("MediaStream Recording")}}

رویداد **`pause`** از رابط {{domxref("MediaRecorder")}} زمانی فعال می‌شود که {{domxref("MediaRecorder.pause()")}} فراخوانی شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pause", (event) => { })

onpause = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

```js
pause.onclick = () => {
  if (mediaRecorder.state === "recording") {
    mediaRecorder.pause();
    // recording paused
  } else if (mediaRecorder.state === "paused") {
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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط رسانه MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): نمایش نمونه MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [نمایش ضبط MediaStream در simpl.info](https://simpl.info/mediarecorder/) توسط [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia")}}