---
title: "CSSGroupingRule: cssRules property"
short-title: cssRules
slug: Web/API/CSSGroupingRule/cssRules
page-type: web-api-instance-property
browser-compat: api.CSSGroupingRule.cssRules
---

{{ APIRef("CSSOM") }}

خاصیت **`cssRules`** از رابط {{domxref("CSSGroupingRule")}} یک {{domxref("CSSRuleList")}} شامل مجموعه‌ای از اشیاء {{domxref("CSSRule")}} برمی‌گرداند.

## مقدار

یک {{domxref("CSSRuleList")}}.

## مثال‌ها

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}