---
title: "ImageTrack: selected property"
---

---
title: "ImageTrack: selected property"
short-title: selected
slug: Web/API/ImageTrack/selected
page-type: web-api-instance-property
browser-compat: api.ImageTrack.selected
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`selected`** از رابط {{domxref("ImageTrack")}}، در صورتی که track برای رمزگشایی انتخاب شده باشد، مقدار `true` را برمی‌گرداند.

## مقدار

یک {{jsxref("Boolean")}}؛ اگر `true` باشد، track برای رمزگشایی انتخاب شده است.

## مثال‌ها

مثال زیر مقدار `selected` را در کنسول چاپ می‌کند.

```js
let track = imageDecoder.tracks.selectedTrack;
console.log(track.selected); // this is the selected track so should return true.
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}