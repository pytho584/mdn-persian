---
title: "MediaList: toString() method"
short-title: toString()
slug: Web/API/MediaList/toString
page-type: web-api-instance-method
browser-compat: api.MediaList.toString
---

{{APIRef("CSSOM")}}

متد **`toString()`** (رشته‌ساز) از رابط {{domxref("MediaList")}} یک رشته (string) شامل مقادیر شیء را برمی‌گرداند. این مقدار یک لیست جدا شده با کاما از مقادیر رسانه است که در قالب مشابه ویژگی {{domxref("MediaList.mediaText")}} می‌باشد.

## نحو

```js-nolint
toString()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک رشته (string).

## مثال‌ها

```js
const firstStyleSheet = document.styleSheets[0]; // the document's first stylesheet
const mediaList = firstStyleSheet.media; // the mediaList of the stylesheet

// set the `media` text to a media query value
mediaList.mediaText = "SCREEN AND (140PX <= WIDTH <= 380PX)";

// add a second media value
mediaList.appendMedium("SCREEN AND (ORIENTATION: LANDSCAPE))");

// erroneously, add the same media query again
mediaList.appendMedium("SCREEN AND (ORIENTATION: LANDSCAPE))");

console.log(mediaList.toString());
// "screen and (140px <= width <= 380px), screen and (orientation: landscape)"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("MediaList.mediaText")}}
- {{domxref("MediaList.appendMedium()")}}
- [Media queries](/en-US/docs/Web/CSS/Guides/Media_queries)
- [Using media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Using)