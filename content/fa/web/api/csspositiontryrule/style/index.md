---
title: "CSSPositionTryRule: style property"
short-title: style
slug: Web/API/CSSPositionTryRule/style
page-type: web-api-instance-property
browser-compat: api.CSSPositionTryRule.style
---

{{ APIRef("CSSOM") }}

ویژگی فقطخواندنی **`style`** در واسط {{domxref("CSSPositionTryRule")}} شامل یک شیء {{domxref("CSSPositionTryDescriptors")}} است که توصیفگرهای موجود در بدنهٔ قاعدهٔ {{cssxref("@position-try")}} را نمایش می‌دهد.

## مقدار

یک شیء {{domxref("CSSPositionTryDescriptors")}}.

اگرچه خود ویژگی `style` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `CSSPositionTryDescriptors` را جایگزین کنید، باز هم می‌توانید مستقیماً به ویژگی `style` مقدار بدهید؛ این کار معادل مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSPositionTryDescriptors` را با استفاده از متدهای {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

CSS شامل یک قاعدهٔ at-rule از نوع `@position-try` با نام `--custom-right` و سه توصیفگر است.

```css
@position-try --custom-bottom {
  top: anchor(bottom);
  min-width: 100px;
  margin-top: 10px;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
const tryOption = myRules[0]; // a CSSPositionTryRule
console.log(tryOption.style.top); // "anchor(bottom)"
console.log(tryOption.style["min-width"]); // "100px"
console.log(tryOption.style.positionArea); // ""; no position-area specified
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("CSSPositionTryDescriptors")}}
- {{cssxref("@position-try")}}
- {{cssxref("position-try-fallbacks")}}
- [موقعیت‌یابی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning) ماژول
- [استفاده از موقعیت‌یابی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
- [مدیریت سرریز: گزینه‌های try و پنهان‌سازی شرطی](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding)
