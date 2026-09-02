---
title: "MediaRecorder: state property"
short-title: state
slug: Web/API/MediaRecorder/state
page-type: web-api-instance-property
browser-compat: api.MediaRecorder.state
---

{{APIRef("MediaStream Recording")}}

ویژگی فقط‌خواندنی **`state`** از رابط {{domxref("MediaRecorder")}} وضعیت فعلی شیء `MediaRecorder` جاری را بازمی‌گرداند.

## مقدار

یک رشته شامل یکی از مقادیر زیر:

- `inactive`
  - : ضبط در حال انجام نیست — یا هنوز شروع نشده است، یا شروع شده و سپس متوقف شده است.
- `recording`
  - : ضبط شروع شده و {{glossary("user agent")}} در حال ضبط داده است.
- `paused`
  - : ضبط شروع شده، سپس مکث شده، اما هنوز متوقف یا از سر گرفته نشده است.

## مثال‌ها

```js
record.onclick = () => {
  mediaRecorder.start();
  console.log(mediaRecorder.state);
  // Will return "recording"
  console.log("recorder started");
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): یک نمایش بصری از MediaRecorder + getUserMedia + Web Audio API، توسط کریس میلز ([کد منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [دموی ضبط MediaStream از simpl.info](https://simpl.info/mediarecorder/)، توسط سام داتن.
- {{domxref("Navigator.getUserMedia()")}}