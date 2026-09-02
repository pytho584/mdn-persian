---
title: "ImageDecoder: complete property"
short-title: complete
slug: Web/API/ImageDecoder/complete
page-type: web-api-instance-property
browser-compat: api.ImageDecoder.complete
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنیِ **`complete`** در رابط {{domxref("ImageDecoder")}}، اگر بافرکردن داده‌های کدگذاری‌شده به پایان رسیده باشد، مقدار `true` را برمی‌گرداند.

## مقدار

یک {{jsxref("Boolean")}}؛ اگر بافرکردن کامل شده باشد، مقدار آن `true` است.

## مثال‌ها

مثال زیر مقدار `complete` را در کنسول چاپ می‌کند.

```js
console.log(imageDecoder.complete);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}