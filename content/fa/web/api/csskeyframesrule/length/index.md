---
title: "CSSKeyframesRule: length property"
short-title: length
slug: Web/API/CSSKeyframesRule/length
page-type: web-api-instance-property
browser-compat: api.CSSKeyframesRule.length
---

{{APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`length`** از رابط {{domxref("CSSKeyframesRule")}} تعداد اشیاء {{domxref("CSSKeyframeRule")}} را در فهرست آن بازمی‌گرداند. سپس می‌توانید هر قانون keyframe را با شاخص (index) آن مستقیماً روی شیء `CSSKeyframeRule` دسترسی پیدا کنید.

## مقدار

یک عدد صحیح غیرمنفی. این مقدار باید برابر با `length` ویژگی {{domxref("CSSKeyframesRule.cssRules", "cssRules")}} باشد.

## مثال‌ها

CSS شامل یک at-rule keyframes است. این اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود.
`myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} بازمی‌گرداند. ویژگی `cssRules` یک {{domxref("CSSRuleList")}} شامل دو قانون بازمی‌گرداند.

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
const myRules = document.styleSheets[0].cssRules;
const keyframes = myRules[0]; // a CSSKeyframesRule
console.log(keyframes.length); // 2
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}