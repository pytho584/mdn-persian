---
title: "ImageDecoder: tracks property"
---

---
title: "ImageDecoder: tracks property"
short-title: tracks
slug: Web/API/ImageDecoder/tracks
page-type: web-api-instance-property
browser-compat: api.ImageDecoder.tracks
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`tracks`** در رابط {{domxref("ImageDecoder")}} فهرستی از trackهای موجود در داده‌های تصویر رمزگذاری‌شده را برمی‌گرداند.

## مقدار

یک شیء {{domxref("ImageTrackList")}}.

## مثال‌ها

مثال زیر مقدار `tracks` را در کنسول چاپ می‌کند. این مقدار یک شیء {{domxref("ImageTrackList")}} خواهد بود.

```js
console.log(imageDecoder.tracks);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}