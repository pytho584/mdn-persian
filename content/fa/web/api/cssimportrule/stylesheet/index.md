---
title: "CSSImportRule: styleSheet property"
---

---
title: "CSSImportRule: styleSheet property"
short-title: styleSheet
slug: Web/API/CSSImportRule/styleSheet
page-type: web-api-instance-property
browser-compat: api.CSSImportRule.styleSheet
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`styleSheet`** از رابط {{domxref("CSSImportRule")}}، شیوه‌نامهٔ CSS تعیین‌شده توسط {{cssxref("@import")}} [قاعدهٔ at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) را برمی‌گرداند. این مقدار در قالب یک شیء {{domxref("CSSStyleSheet")}} خواهد بود.

یک [قاعدهٔ at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) با {{cssxref("@import")}} همیشه یک شیوه‌نامهٔ مرتبط دارد.

## مقدار

یک {{domxref("CSSStyleSheet")}}.

## مثال‌ها

شیوه‌نامهٔ زیر شامل یک قاعدهٔ {{cssxref("@import")}} است. بنابراین نخستین مورد در فهرست قواعد CSS یک `CSSImportRule` خواهد بود. ویژگی `styleSheet` شیوه‌نامهٔ واردشده را برمی‌گرداند.

```css
@import "style.css" screen;
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].styleSheet); // A CSSStyleSheet
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}