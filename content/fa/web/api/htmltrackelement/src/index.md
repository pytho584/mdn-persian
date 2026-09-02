---
title: "HTMLTrackElement: src property"
short-title: src
slug: Web/API/HTMLTrackElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.src
---

{{APIRef("HTML DOM")}}

ویژگی **`src`** از رابط {{domxref("HTMLTrackElement")}} مقدار ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/track#src) عنصر {{HTMLElement("track")}} را منعکس می‌کند. این ویژگی نشانی اینترنتی (URL) داده‌های مسیر متنی (text track) را مشخص می‌کند.

## مقدار

یک رشته (string) شامل نشانی اینترنتی داده‌های مسیر متنی.

## مثال

```js
const trackElement = document.getElementById("exampleTrack");
console.log(`Track's URL: ${trackElement.src}`);
trackElement.src = "newTrack.vtt";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTrackElement")}}
- {{HTMLElement("track")}}