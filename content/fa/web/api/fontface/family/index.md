---
title: "FontFace: family property"
short-title: family
slug: Web/API/FontFace/family
page-type: web-api-instance-property
browser-compat: api.FontFace.family
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

ویژگی **`FontFace.family`** به نویسنده اجازه می‌دهد تا خانواده فونت یک شیء {{domxref("FontFace")}} را دریافت یا تنظیم کند.

این مقدار برای تطبیق نام با یک فونت خاص هنگام استایل‌دهی به عناصر با استفاده از ویژگی {{cssxref("font-family")}} استفاده می‌شود.
هر نامی می‌تواند استفاده شود و این نام، هر نامی را که در داده‌های اصلی فونت مشخص شده است، لغو می‌کند.

این ویژگی معادل توصیف‌گر {{cssxref("@font-face/font-family", "font-family")}} در {{cssxref("@font-face")}} است.

## مقدار

یک رشته (string).

## مثال‌ها

```js
let fontFace = new FontFace(
  "Roboto",
  'url("https://fonts.example.com/roboto.woff2")',
);
console.log(fontFace.family); // 'Roboto'

fontFace.family = "newRoboto";
console.log(fontFace.family); // 'newRoboto'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}