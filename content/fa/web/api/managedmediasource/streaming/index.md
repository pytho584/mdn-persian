```
---
title: "ManagedMediaSource: streaming property"
short-title: streaming
slug: Web/API/ManagedMediaSource/streaming
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ManagedMediaSource.streaming
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`streaming`** در رابط {{domxref("ManagedMediaSource")}} یک مقدار بولی است که نشان می‌دهد آیا برنامه باید به‌طور فعال داده‌های رسانه‌ای را دریافت و اضافه کند.

مقدار این ویژگی توسط الگوریتم پایش عامل کاربر (user agent) به‌روزرسانی می‌شود. وقتی این مقدار تغییر کند، رویداد متناظر {{domxref("ManagedMediaSource.startstreaming_event", "startstreaming")}} یا {{domxref("ManagedMediaSource.endstreaming_event", "endstreaming")}} پرتاب می‌شود.

## مقدار

یک مقدار بولی که در ابتدا `false` است. وقتی `true` باشد، عامل کاربر برای تضمین پخش بدون وقفه به داده‌های بیشتری نیاز دارد. وقتی `false` باشد، عامل کاربر داده‌های کافی در بافر دارد و برنامه می‌تواند از دریافت سگمنت‌های جدید خودداری کند.

## مثال‌ها

### بررسی وضعیت streaming

این مثال یک {{domxref("ManagedMediaSource")}} می‌سازد، آن را به یک عنصر {{htmlelement("video")}} متصل می‌کند و هر بار که مقدار `streaming` بین `true` و `false` تغییر کند، آن را در لاگ ثبت می‌کند.

```js
const mediaType = 'video/mp4; codecs="avc1.64001F, mp4a.40.2"';

if (ManagedMediaSource.isTypeSupported(mediaType)) {
  const video = document.createElement("video");
  const source = new ManagedMediaSource();

  video.controls = true;
  video.disableRemotePlayback = true;
  video.src = URL.createObjectURL(source);
  document.body.appendChild(video);

  console.log(source.streaming); // false

  source.addEventListener("startstreaming", () => {
    console.log(source.streaming); // true — start fetching data
  });

  source.addEventListener("endstreaming", () => {
    console.log(source.streaming); // false — stop fetching data
  });

  source.addEventListener("sourceopen", () => {
    source.addSourceBuffer(mediaType);
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("ManagedMediaSource.startstreaming_event", "startstreaming")}}
- رویداد {{domxref("ManagedMediaSource.endstreaming_event", "endstreaming")}}
- {{domxref("ManagedMediaSource")}}
- {{domxref("MediaSource")}}
```