---
title: "HTMLTrackElement: srclang property"
short-title: srclang
slug: Web/API/HTMLTrackElement/srclang
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.srclang
---

{{APIRef("HTML DOM")}}

ویژگی **`srclang`** در رابط {{domxref("HTMLTrackElement")}} مقدارِ ویژگی [`srclang`](/en-US/docs/Web/HTML/Reference/Elements/track#srclang) عنصر {{HTMLElement("track")}} را منعکس می‌کند؛ اگر این ویژگی تعریف نشده باشد، رشتهٔ خالی برمی‌گرداند.

ویژگی `srclang` یک {{glossary("BCP 47 language tag")}} است و زبان داده‌های text track را مشخص می‌کند.

## مقدار

یک رشته.

## مثال

```js
const trackElement = document.getElementById("exampleTrack");
console.log(`Track's language: ${trackElement.srclang}`);
trackElement.srclang = "en-US";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTrackElement")}}
- {{HTMLElement("track")}}