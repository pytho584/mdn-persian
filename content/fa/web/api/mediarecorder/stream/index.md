---
title: "MediaRecorder: stream property"
short-title: stream
slug: Web/API/MediaRecorder/stream
page-type: web-api-instance-property
browser-compat: api.MediaRecorder.stream
---

{{APIRef("MediaStream Recording")}}

ویژگی **`stream`** از رابط {{domxref("MediaRecorder")}} که فقط‌خواندنی است، جریانی (stream) را بازمی‌گرداند که هنگام ایجاد `MediaRecorder` به سازندهٔ {{domxref("MediaRecorder.MediaRecorder", "MediaRecorder()")}} ارسال شده بود.

## مقدار

همان {{domxref("MediaStream")}} که هنگام ایجاد اولیهٔ `MediaRecorder` به سازندهٔ `MediaRecorder()` ارسال شده است.

## مثال‌ها

```js
if (navigator.getUserMedia) {
  console.log("getUserMedia supported.");
  navigator.getUserMedia(
    // constraints - only audio needed for this app
    {
      audio: true,
    },

    // Success callback
    (stream) => {
      const mediaRecorder = new MediaRecorder(stream);

      const myStream = mediaRecorder.stream;
      console.log(myStream);
    },
  );
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): دموی ضبط با MediaRecorder + getUserMedia + تجسم Web Audio API، نوشتهٔ [Chris Mills](https://github.com/chrisdavidmills) ([کد منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [دموی ضبط MediaStream در simpl.info](https://simpl.info/mediarecorder/)، نوشتهٔ [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia")}}