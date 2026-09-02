---
title: "MediaStream: id property"
short-title: id
slug: Web/API/MediaStream/id
page-type: web-api-instance-property
browser-compat: api.MediaStream.id
---

{{APIRef("Media Capture and Streams")}}

ویژگی فقط‌خواندنی **`id`** در رابط {{domxref("MediaStream")}}، رشته‌ای متشکل از ۳۶ نویسه است که شناسهٔ یکتا (GUID) را برای این شیء مشخص می‌کند.

## مقدار

یک رشته.

## مثال‌ها

```js
const promise = navigator.mediaDevices.getUserMedia({
  audio: true,
  video: true,
});

promise.then((stream) => {
  console.log(stream.id);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaStream")}}، رابطی که این ویژگی به آن تعلق دارد.