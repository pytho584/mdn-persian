---
title: "CSSStyleSheet: ownerRule property"
short-title: ownerRule
slug: Web/API/CSSStyleSheet/ownerRule
page-type: web-api-instance-property
browser-compat: api.CSSStyleSheet.ownerRule
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`ownerRule`** از رابط {{domxref("CSSStyleSheet")}}، شیء {{domxref("CSSImportRule")}} متناظر با قاعده at-rule مربوط به {{cssxref("@import")}} را برمی‌گرداند که برگه سبک را به سند وارد کرده است. اگر برگه سبک با استفاده از `@import` وارد سند نشده باشد، مقدار بازگشتی `null` است.

## مقدار

یک {{domxref("CSSImportRule")}} متناظر با قاعده {{cssxref("@import")}} که برگه سبک را به سند وارد کرده است. اگر برگه سبک با استفاده از `@import` وارد سند نشده باشد، مقدار بازگشتی `null` است.

## مثال‌ها

این قطعه کد به دنبال قواعدی می‌گردد که با استفاده از قاعده at-rule مربوط به `@import` وارد سند نشده‌اند.

```js
const ruleList = document.styleSheets[0].cssRules;

for (const rule of ruleList) {
  if (!rule.ownerRule) {
    /* قاعده وارد نشده است */
  }
}
```

این قطعه مرجعی از برگه سبک مرتبط با `@import` به دست می‌آورد و آن را به‌نحوی پردازش می‌کند:

```js
const ruleList = document.styleSheets[0].cssRules;

for (const rule of ruleList) {
  if (rule.ownerRule) {
    checkStylesheet(rule.ownerRule.styleSheet);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model)
- [استفاده از اطلاعات سبک‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)
```