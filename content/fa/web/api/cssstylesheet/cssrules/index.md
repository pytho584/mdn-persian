---
title: "CSSStyleSheet: cssRules property"
---

---
title: "CSSStyleSheet: cssRules property"
short-title: cssRules
slug: Web/API/CSSStyleSheet/cssRules
page-type: web-api-instance-property
browser-compat: api.CSSStyleSheet.cssRules
---

{{APIRef("CSSOM")}}

خاصیت فقط‌خواندنی {{domxref("CSSStyleSheet")}} با نام **`cssRules`** یک {{domxref("CSSRuleList")}} زنده بازمی‌گرداند که فهرستی بی‌درنگ و به‌روز از تمام قواعد CSS تشکیل‌دهندهٔ شیوه‌نامه ارائه می‌دهد. هر آیتم در این فهرست یک {{domxref("CSSRule")}} است که یک قاعدهٔ واحد را تعریف می‌کند.

## مقدار

یک {{domxref("CSSRuleList")}} که به‌صورت زنده به‌روز می‌شود و شامل تک‌تک قواعد CSS سازندهٔ شیوه‌نامه است. هر ورودی در فهرست قواعد، یک شیء {{domxref("CSSRule")}} است که یک قاعده از قواعد سازندهٔ شیوه‌نامه را توصیف می‌کند.

## مثال‌ها

سپس می‌توان قواعد تکی داخل شیوه‌نامه را با ایندکس (اندیس) در دسترس قرار داد:

```js
const ruleList = document.styleSheets[0].cssRules;

for (let i = 0; i < ruleList.length; i++) {
  processRule(ruleList[i]);
}
```

قواعد را می‌توان با {{jsxref("Statements/for...of", "for...of")}} نیز در دسترس قرار داد:

```js
const ruleList = document.styleSheets[0].cssRules;

for (const rule of ruleList) {
  processRule(rule);
}
```

با این حال، چون `CSSRule` یک آرایهٔ واقعی نیست، نمی‌توانید از {{jsxref("Array.forEach", "forEach()")}} استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model)
- [Using dynamic styling information](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)