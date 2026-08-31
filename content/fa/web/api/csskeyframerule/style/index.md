---
title: "CSSKeyframeRule: style property"
short-title: style
slug: Web/API/CSSKeyframeRule/style
page-type: web-api-instance-property
browser-compat: api.CSSKeyframeRule/style
---

{{ APIRef("CSSOM") }}

ویژگی **`style`** فقط‌خواندنی رابط {{domxref("CSSKeyframeRule")}} شامل یک شیء {{domxref("CSSStyleDeclaration")}} است که توصیفگرهای موجود در بدنهٔ قانون {{cssxref("@keyframes")}} را نشان می‌دهد.

## مقدار

یک شیء {{domxref("CSSStyleDeclaration")}}.

اگرچه خود ویژگی **`style`** از این نظر فقط‌خواندنی است که نمی‌توانید شیء `CSSStyleDeclaration` را جایگزین کنید، همچنان می‌توانید مستقیماً به ویژگی `style` مقدار اختصاص دهید که معادل مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSStyleDeclaration` را با استفاده از متدهای {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

CSS شامل یک at-rule به نام {{cssxref("@keyframes")}} است. این اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود. `myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} برمی‌گرداند که شامل شیءهای جداگانه‌ای از نوع {{domxref("CSSKeyFrameRule")}} برای هر keyframe خواهد بود.

```css
@keyframes slide-in {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
let keyframes = myRules[0]; // a CSSKeyframesRule
console.log(keyframes[0].style); // a CSSStyleDeclaration
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}