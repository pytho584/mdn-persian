---
title: "CSSCounterStyleRule: pad property"
short-title: pad
slug: Web/API/CSSCounterStyleRule/pad
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.pad
---

{{APIRef("CSSOM")}}

ویژگی **`pad`** از رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیفگر {{cssxref("@counter-style/pad", "pad")}} را دریافت و تنظیم می‌کند. اگر برای این توصیفگر مقداری تعیین نشده باشد، این ویژگی یک رشته خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همان قانون `@counter-style` است و بازگرداندن `pad` مقدار «0» را به ما می‌دهد.

```css
@counter-style box-corner {
  system: numeric;
  symbols: "0" "1" "2" "3" "4" "5";
  pad: 2 "0";
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].pad); // "0"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}