---
title: "CSSRuleList: length property"
short-title: length
slug: Web/API/CSSRuleList/length
page-type: web-api-instance-property
browser-compat: api.CSSRuleList.length
---

{{ APIRef("CSSOM") }}

خاصیت **`length`** در رابط {{domxref("CSSRuleList")}} تعداد اشیاء {{domxref("CSSRule")}} موجود در فهرست را برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، تعداد آیتم‌های موجود در {{domxref("CSSRuleList")}} به نام `myRules` در کنسول چاپ می‌شود.

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules.length);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}