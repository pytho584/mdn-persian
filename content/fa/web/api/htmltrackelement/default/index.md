---
title: "HTMLTrackElement: default property"
short-title: default
slug: Web/API/HTMLTrackElement/default
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.default
---

{{ApiRef("HTML DOM")}}

ویژگی **`default`** در رابط {{domxref("HTMLTrackElement")}} مشخص می‌کند که آیا track در صورتی فعال می‌شود که تنظیمات کاربر نشان ندهد track دیگری مناسب‌تر است. این ویژگی، صفت بولین [`default`](/en-US/docs/Web/HTML/Reference/Elements/track#default) عنصر {{htmlelement("track")}} را منعکس می‌کند؛ اگر این صفت وجود داشته باشد مقدار `true` و در غیر این صورت مقدار `false` برمی‌گرداند.

## مقدار

یک مقدار بولین.

## مثال

```js
const trackElement = document.getElementById("exampleTrack");
console.log(trackElement.default);
trackElement.default = true;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTrackElement.kind")}}
- {{domxref("HTMLTrackElement.label")}}
