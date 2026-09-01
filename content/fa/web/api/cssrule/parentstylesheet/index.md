---
title: "CSSRule: parentStyleSheet property"
short-title: parentStyleSheet
slug: Web/API/CSSRule/parentStyleSheet
page-type: web-api-instance-property
browser-compat: api.CSSRule.parentStyleSheet
---

{{ APIRef("CSSOM") }}

ویژگی **`parentStyleSheet`** در رابط {{domxref("CSSRule")}}، شیء {{domxref("StyleSheet")}}ای را برمیگرداند که قانون (rule) جاری در آن تعریف شده است.

## مقدار

یک شیء {{domxref("StyleSheet")}}.

## مثالها

```js
const docRules = document.styleSheets[0].cssRules;
console.log(docRules[0].parentStyleSheet === document.styleSheets[0]); // returns true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}