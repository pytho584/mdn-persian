---
title: "FontFace: descentOverride property"
short-title: descentOverride
slug: Web/API/FontFace/descentOverride
page-type: web-api-instance-property
browser-compat: api.FontFace.descentOverride
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

ویژگی **`descentOverride`** از رابط {{domxref("FontFace")}} مقدار توصیف‌کننده {{cssxref("@font-face/descent-override")}} را برمی‌گرداند و تنظیم می‌کند. مقادیر ممکن عبارتند از `normal` که نشان می‌دهد معیار مورد استفاده باید از فایل فونت دریافت شود، یا یک درصد.

## مقدار

یک رشته.

## مثال‌ها

```js
let fontFace = new FontFace(
  "Roboto",
  'url("https://fonts.example.com/roboto.woff2")',
  { descentOverride: "90%" },
);
console.log(fontFace.descentOverride); // 90%
fontFace.descentOverride = "normal";
console.log(fontFace.descentOverride); // 'normal'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}