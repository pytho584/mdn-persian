---
title: "MediaList: length property"
short-title: length
slug: Web/API/MediaList/length
page-type: web-api-instance-property
browser-compat: api.MediaList.length
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`length`** در رابط {{DOMxRef("MediaList")}} تعداد کوئری‌های رسانه‌ای موجود در فهرست را برمی‌گرداند.

## مقدار

یک عدد صحیح مثبت.

## مثال‌ها

در مثال زیر، تعداد کوئری‌های رسانه‌ای ذخیره‌شده در `MediaList` مربوط به اولین stylesheet اعمال‌شده به سند فعلی، در کنسول ثبت می‌شود.

```js
const stylesheets = document.styleSheets;
const stylesheet = stylesheets[0];
console.log(stylesheet.media.length);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}