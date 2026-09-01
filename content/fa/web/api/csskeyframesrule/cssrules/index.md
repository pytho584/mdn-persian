---
title: "CSSKeyframesRule: cssRules property"
short-title: cssRules
slug: Web/API/CSSKeyframesRule/cssRules
page-type: web-api-instance-property
browser-compat: api.CSSKeyframesRule.cssRules
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`cssRules`** در رابط {{domxref("CSSKeyframeRule")}} یک {{domxref("CSSRuleList")}} شامل قواعد موجود در [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) کادر‌های کلیدی (keyframes) را بازمی‌گرداند.

> [!NOTE]
> خود شیء `CSSKeyframeRule` مانند یک آرایه قابل ایندکس‌گذاری است و رفتاری مشابه ویژگی `cssRules` آن دارد.

## مقدار

یک {{domxref('CSSRuleList')}}.

## مثال‌ها

CSS شامل یک at-rule کادر‌های کلیدی است. این at-rule، اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` برگردانده می‌شود.
`myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} را برمی‌گرداند. ویژگی `cssRules` یک {{domxref("CSSRuleList")}} شامل دو قاعده را برمی‌گرداند.

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
console.log(keyframes.cssRules); // a CSSRuleList object with two rules
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}