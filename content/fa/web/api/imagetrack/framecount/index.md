```yaml
---
title: "ImageTrack: frameCount property"
short-title: frameCount
slug: Web/API/ImageTrack/frameCount
page-type: web-api-instance-property
browser-compat: api.ImageTrack.frameCount
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`frameCount`** از رابط {{domxref("ImageTrack")}} تعداد فریم‌های موجود در track را بازمی‌گرداند.

## مقدار

یک عدد صحیح (integer).

## مثال‌ها

مثال زیر مقدار `frameCount` را در کنسول چاپ می‌کند.

```js
let track = imageDecoder.tracks.selectedTrack;
console.log(track.frameCount);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```