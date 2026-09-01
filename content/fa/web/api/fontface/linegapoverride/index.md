---
title: "FontFace: lineGapOverride property"
short-title: lineGapOverride
slug: Web/API/FontFace/lineGapOverride
page-type: web-api-instance-property
browser-compat: api.FontFace.lineGapOverride
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

ویژگی **`lineGapOverride`** از رابط {{domxref("FontFace")}} مقدار توصیف‌گر {{cssxref("@font-face/line-gap-override")}} را برمی‌گرداند و تنظیم می‌کند.
مقادیر ممکن عبارت‌اند از `normal`، که نشان می‌دهد معیار استفاده‌شده باید از فایل فونت به دست آید، یا یک درصد.

## مقدار

یک رشته.

## نمونه‌ها

```js
let fontFace = new FontFace(
  "Roboto",
  'url("https://fonts.example.com/roboto.woff2")',
  { lineGapOverride: "90%" },
);
console.log(fontFace.lineGapOverride); // 90%
fontFace.lineGapOverride = "normal";
console.log(fontFace.lineGapOverride); // 'normal'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}