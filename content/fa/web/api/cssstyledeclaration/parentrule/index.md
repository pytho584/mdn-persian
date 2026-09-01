---
title: "CSSStyleDeclaration: parentRule property"
short-title: parentRule
slug: Web/API/CSSStyleDeclaration/parentRule
page-type: web-api-instance-property
browser-compat: api.CSSStyleDeclaration.parentRule
---

{{ APIRef("CSSOM") }}

خاصیت فقط‌خواندنی **CSSStyleDeclaration.parentRule** یک {{domxref('CSSRule')}} برمی‌گرداند که والد این بلوک سبک است؛ مثلاً یک {{domxref('CSSStyleRule')}} که سبک مربوط به یک انتخابگر CSS را نمایش می‌دهد.

## مقدار

قانون CSS که شامل این بلوک اعلان است، یا اگر این {{domxref('CSSStyleDeclaration')}} به هیچ {{domxref('CSSRule')}} ای متصل نباشد، مقدار `null` برمی‌گرداند.

## مثال‌ها

کد جاوااسکریپت زیر قانون سبک والد را از یک {{domxref('CSSStyleDeclaration')}} دریافت می‌کند:

```js
const declaration = document.styleSheets[0].rules[0].style;
const rule = declaration.parentRule;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}