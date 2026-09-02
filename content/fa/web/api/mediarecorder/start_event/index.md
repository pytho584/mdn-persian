---
title: "MediaRecorder: start event"
short-title: start
slug: Web/API/MediaRecorder/start_event
page-type: web-api-event
browser-compat: api.MediaRecorder.start_event
---

{{APIRef("MediaStream Recording")}}

رویداد **`start`** از رابط {{domxref("MediaRecorder")}} زمانی فعال می‌شود که متد {{domxref("MediaRecorder.start()")}} فراخوانی شود. در این نقطه، داده‌ها شروع به جمع‌آوری در یک {{domxref("Blob")}} می‌کنند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("start", (event) => { })

onstart = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Example

```js
record.onclick = () => {
  mediaRecorder.start();
  console.log("recorder started");
};

mediaRecorder.onstart = () => {
  // do something in response to
  // recording being started
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از API ضبط جریان رسانه](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): نمایشی از MediaRecorder + getUserMedia + Web Audio API به همراه مصورسازی، توسط [Chris Mills](https://github.com/chrisdavidmills) ([کد منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone))
- [نمایش ضبط MediaStream در simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton)
- {{domxref("Navigator.getUserMedia")}}