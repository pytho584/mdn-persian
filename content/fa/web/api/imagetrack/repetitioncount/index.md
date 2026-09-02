---
title: "ImageTrack: repetitionCount property"
short-title: repetitionCount
slug: Web/API/ImageTrack/repetitionCount
page-type: web-api-instance-property
browser-compat: api.ImageTrack.repetitionCount
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`repetitionCount`** در رابط {{domxref("ImageTrack")}} تعداد تکرارهای این ترک را برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

مثال زیر مقدار `repetitionCount` را در کنسول چاپ می‌کند.

```js
let track = imageDecoder.tracks.selectedTrack;
console.log(track.repetitionCount);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}