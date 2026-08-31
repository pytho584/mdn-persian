---
title: "CSSImportRule: supportsText property"
short-title: supportsText
slug: Web/API/CSSImportRule/supportsText
page-type: web-api-instance-property
browser-compat: api.CSSImportRule.supportsText
---

{{APIRef("CSSOM")}}

ویژگی فقط‑خواندنی **`supportsText`** از رابط {{domxref("CSSImportRule")}} شرط پشتیبانی‌ای را که توسط [قاعده at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) {{cssxref("@import")}} مشخص شده است، بازمی‌گرداند.

## مقدار

یک رشته، یا `null`.

## مثال‌ها

شیوه‌نامهٔ واحد سند شامل سه قاعدهٔ {{cssxref("@import")}} است. اولین اعلان یک شیوه‌نامه را در صورت پشتیبانی از `display: flex` وارد می‌کند. دومین اعلان یک شیوه‌نامه را در صورت پشتیبانی از انتخابگر `:has` وارد می‌کند. سومین اعلان یک شیوه‌نامه را بدون شرط پشتیبانی وارد می‌کند. ویژگی `supportsText` شرایط واردات مرتبط با قاعده at را بازمی‌گرداند.

```css
@import "style1.css" supports(display: flex);
@import "style2.css" supports(selector(p:has(a)));
@import "style3.css";
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].supportsText); // returns `"display: flex"`
console.log(myRules[1].supportsText); // returns `"selector(p:has(a))"`
console.log(myRules[2].supportsText); // returns `null`
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پرس‌وجوهای ویژگی](/en-US/docs/Web/CSS/Guides/Conditional_rules/Using_feature_queries)
- {{cssxref("@import")}} و {{cssxref("@supports")}}