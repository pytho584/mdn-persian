---
title: "FontFace: ascentOverride property"
short-title: ascentOverride
slug: Web/API/FontFace/ascentOverride
page-type: web-api-instance-property
browser-compat: api.FontFace.ascentOverride
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

ویژگی **`ascentOverride`** از رابط {{domxref("FontFace")}}، معیار بالای خط (ascent) را برای فونت بازمی‌گرداند و تنظیم می‌کند؛ این معیار ارتفاع بالای خط پایه (baseline) است که CSS برای چیدمان جعبه‌های خط (line boxes) در یک بافت قالب‌بندی درون‌خطی (inline formatting context) استفاده می‌کند.

این ویژگی معادل توصیفگر {{cssxref("@font-face/ascent-override")}} در {{cssxref("@font-face")}} است.

## مقدار

یک رشته. مقادیر ممکن `normal` است، به این معنی که معیار مورد استفاده باید از فایل فونت گرفته شود، یا یک درصد.

این ویژگی مقادیر مشابه توصیفگر {{cssxref("@font-face/ascent-override")}} را می‌پذیرد.

## مثال‌ها

```js
let fontFace = new FontFace(
  "Roboto",
  'url("https://fonts.example.com/roboto.woff2")',
  { ascentOverride: "90%" },
);
console.log(fontFace.ascentOverride); // 90%
fontFace.ascentOverride = "normal";
console.log(fontFace.ascentOverride); // 'normal'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}