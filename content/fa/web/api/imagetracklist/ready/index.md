---
title: "ImageTrackList: ready property"
---

---
title: "ImageTrackList: ready property"
short-title: ready
slug: Web/API/ImageTrackList/ready
page-type: web-api-instance-property
browser-compat: api.ImageTrackList.ready
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`ready`** در رابط {{domxref("ImageTrackList")}} یک {{jsxref("Promise")}} برمی‌گرداند که وقتی `ImageTrackList` با {{domxref("ImageTrack","tracks")}} پر می‌شود، حل می‌شود.

## Value

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود.

## Examples

مثال زیر مقدار `ready` را در کنسول چاپ می‌کند؛ این مقدار پس از اینکه promise حل شود، `undefined` خواهد بود.

```js
let tracks = imageDecoder.tracks;
let ready = await tracks.ready;
console.log(ready);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}