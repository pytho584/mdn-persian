---
title: "CSSImportRule: layerName property"
short-title: layerName
slug: Web/API/CSSImportRule/layerName
page-type: web-api-instance-property
browser-compat: api.CSSImportRule.layerName
---

{{APIRef("CSSOM")}}

ویژگی فقط‑خواندنی **`layerName`** از رابط {{domxref("CSSImportRule")}} نام لایهٔ آبشاری ایجاد شده توسط [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) {{cssxref("@import")}} را برمی‌گرداند.

اگر لایهٔ ایجاد شده ناشناس (anonymous) باشد، رشته خالی (`""`) است؛ اگر هیچ لایه‌ای ایجاد نشده باشد، شیء `null` است.

## مقدار

یک رشته که می‌تواند خالی باشد، یا شیء `null`.

## مثال‌ها

شیوه‌نامهٔ (stylesheet) تنها سند شامل سه قاعدهٔ {{cssxref("@import")}} است. اعلام اول یک شیوه‌نامه را به یک لایهٔ نام‌دار (named layer) وارد می‌کند. اعلام دوم یک شیوه‌نامه را به یک لایهٔ ناشناس (anonymous layer) وارد می‌کند. اعلام سوم یک شیوه‌نامه را بدون اعلام لایه وارد می‌کند.

ویژگی `layerName` نام لایهٔ مرتبط با شیوه‌نامهٔ وارد شده را برمی‌گرداند.

```css
@import "style1.css" layer(layer-1);
@import "style2.css" layer;
@import "style3.css";
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].layerName); // returns `"layer-1"`
console.log(myRules[1].layerName); // returns `""` (an anonymous layer)
console.log(myRules[2].layerName); // returns `null`
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- ناحیهٔ یادگیری: [لایه‌های آبشاری](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers)
- {{cssxref("@import")}} و {{cssxref("@layer")}}