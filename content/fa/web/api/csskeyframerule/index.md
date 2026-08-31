---
title: CSSKeyframeRule
slug: Web/API/CSSKeyframeRule
page-type: web-api-interface
browser-compat: api.CSSKeyframeRule
---

{{APIRef("CSSOM")}}

رابطه (interface) **`CSSKeyframeRule`** یک شیء را توصیف می‌کند که مجموعه‌ای از سبک‌ها برای یک keyframe مشخص را نشان می‌دهد. این رابط معادل محتویات یک keyframe تکی از یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) {{cssxref("@keyframes")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

_ویژگی‌های مربوط به رابطه (interface) والد خود یعنی {{domxref("CSSRule")}} را به ارث می‌برد._

- {{domxref("CSSKeyframeRule.keyText")}}
  - : کلید keyframe را نشان می‌دهد، مانند `'10%'` یا `'75%'`. کلمه کلیدی `from` به `'0%'` و کلمه کلیدی `to` به `'100%'` نگاشت می‌شود.
- {{domxref("CSSKeyframeRule.style")}} {{ReadOnlyInline}}
  - : یک {{domxref("CSSStyleDeclaration")}} از سبک CSS مرتبط با keyframe را برمی‌گرداند.

## روش‌های نمونه (Instance methods)

_روش خاصی ندارد؛ روش‌های مربوط به رابطه والد خود یعنی {{domxref("CSSRule")}} را به ارث می‌برد._

## مثال‌ها

CSS شامل یک at-rule keyframes است. این اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` برگردانده می‌شود. `myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} را برمی‌گرداند که شامل اشیاء `CSSKeyFrameRule` جداگانه برای هر keyframe است.

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
let keyframes = myRules[0]; // یک CSSKeyframesRule
console.log(keyframes[0]); // یک CSSKeyframeRule که یک keyframe تکی را نشان می‌دهد.
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@keyframes")}}
- {{domxref("CSSKeyFramesRule")}}