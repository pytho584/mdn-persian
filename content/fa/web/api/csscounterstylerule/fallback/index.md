---
title: "CSSCounterStyleRule: fallback property"
short-title: fallback
slug: Web/API/CSSCounterStyleRule/fallback
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.fallback
---

{{APIRef("CSSOM")}}

ویژگی **`fallback`** از رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیفگر {{cssxref("@counter-style/fallback","fallback")}} را دریافت و تنظیم میکند. اگر برای این توصیفگر مقدار تعیین نشده باشد، این ویژگی یک رشتهی خالی برمیگرداند.

## مقدار

یک رشته.

## مثالها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان میدهد. در جاوااسکریپت، `myRules[0]` همین قانون `@counter-style` است و بازگرداندن `fallback` مقدار «disc» را به ما میدهد.

```css
@counter-style box-corner {
  system: fixed;
  symbols: ◰ ◳ ◲ ◱;
  suffix: ": ";
  fallback: disc;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].fallback); // "disc"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}