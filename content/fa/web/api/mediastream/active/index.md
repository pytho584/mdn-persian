---
title: "MediaStream: active property"
short-title: active
slug: Web/API/MediaStream/active
page-type: web-api-instance-property
browser-compat: api.MediaStream.active
---

{{APIRef("Media Capture and Streams")}}

ویژگی فقط‌خواندنی **`active`** در رابط {{domxref("MediaStream")}} یک مقدار بولین (Boolean) برمی‌گرداند که اگر جریان (stream) در حال حاضر فعال باشد، `true` و در غیر این صورت `false` است. یک جریان زمانی **فعال** در نظر گرفته می‌شود که حداقل یکی از {{domxref("MediaStreamTrack")}}های آن دارای ویژگی {{domxref("MediaStreamTrack.readyState")}} با مقدار `ended` نباشد. به محض اینکه همهٔ trackها به پایان برسند، ویژگی `active` جریان به `false` تبدیل می‌شود.

## مقدار

یک مقدار بولین که اگر جریان در حال حاضر فعال باشد `true` و در غیر این صورت `false` است.

## مثال‌ها

در این مثال، یک جریان جدید که منبع آن دوربین و میکروفون محلی کاربر است، با استفاده از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} درخواست می‌شود. وقتی آن جریان در دسترس قرار می‌گیرد (یعنی وقتی {{jsxref("Promise")}} برگشتی fulfilled می‌شود)، یک دکمه در صفحه بر اساس فعال بودن یا نبودن جریان به‌روزرسانی می‌شود.

```js
const promise = navigator.mediaDevices.getUserMedia({
  audio: true,
  video: true,
});

promise.then((stream) => {
  const startBtn = document.querySelector("#startBtn");
  startBtn.disabled = stream.active;
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}