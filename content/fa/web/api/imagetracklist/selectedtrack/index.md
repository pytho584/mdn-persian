---
title: "ImageTrackList: selectedTrack property"
---

---
title: "ImageTrackList: selectedTrack property"
short-title: selectedTrack
slug: Web/API/ImageTrackList/selectedTrack
page-type: web-api-instance-property
browser-compat: api.ImageTrackList.selectedTrack
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`selectedTrack`** از رابط {{domxref("ImageTrackList")}} یک شیء {{domxref("ImageTrack")}} برمی‌گرداند که نشان‌دهندهٔ track انتخاب‌شدهٔ فعلی است.

## مقدار

یک شیء {{domxref("ImageTrack")}}.

## مثال‌ها

مثال زیر `selectedTrack` را برمی‌گرداند و آن را در کنسول چاپ می‌کند.

```js
let track = imageDecoder.tracks.selectedTrack;
console.log(track);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}