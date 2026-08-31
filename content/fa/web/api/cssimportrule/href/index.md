---
title: "CSSImportRule: href property"
short-title: href
slug: Web/API/CSSImportRule/href
page-type: web-api-instance-property
browser-compat: api.CSSImportRule.href
---

{{APIRef("CSSOM")}}

خاصیت فقط‑خواندنی **`href`** از رابط {{domxref("CSSImportRule")}}، نشانی اینترنتی (URL) مشخص‌شده توسط {{cssxref("@import")}} [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) را برمی‌گرداند.

نشانی اینترنتی تفکیک‌شده (resolved URL) همان ویژگی [`href`](/en-US/docs/Web/HTML/Reference/Elements/link#href) sheet سبک مرتبط خواهد بود.

## مقدار

یک رشته (string).

## نمونه‌ها

sheet سبک زیر شامل یک قانون {{cssxref("@import")}} است. بنابراین اولین آیتم در فهرست قوانین CSS یک `CSSImportRule` خواهد بود. خاصیت `href` نشانی اینترنتی sheet سبک واردشده را برمی‌گرداند.

```css
@import "style.css" screen;
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].href); // 'style.css'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}