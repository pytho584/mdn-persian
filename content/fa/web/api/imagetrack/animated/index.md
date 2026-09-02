---
title: "ImageTrack: animated property"
short-title: animated
slug: Web/API/ImageTrack/animated
page-type: web-api-instance-property
browser-compat: api.ImageTrack.animated
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`animated`** از رابط {{domxref("ImageTrack")}} اگر track متحرک باشد و بنابراین فریم‌های متعددی داشته باشد، مقدار `true` را برمی‌گرداند.

## مقدار

یک {{jsxref("Boolean")}}؛ اگر `true` باشد، این یک track متحرک است.

## مثال‌ها

مثال زیر مقدار `animated` را در کنسول چاپ می‌کند.

```js
let track = imageDecoder.tracks.selectedTrack;
console.log(track.animated);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```