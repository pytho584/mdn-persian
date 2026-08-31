---
title: "CSSCounterStyleRule: symbols property"
short-title: symbols
slug: Web/API/CSSCounterStyleRule/symbols
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.symbols
---

{{APIRef("CSSOM")}}

ویژگی **`symbols`** از رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیفگر {{cssxref("@counter-style/symbols","symbols")}} را دریافت و تنظیم می‌کند. اگر توصیفگر مقدار تنظیم‌شده‌ای نداشته باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همین قانون `@counter-style` است و `symbols` مقدار «◰ ◳ ◲ ◱» را برمی‌گرداند.

```css
@counter-style box-corner {
  system: fixed;
  symbols: ◰ ◳ ◲ ◱;
  suffix: ": ";
  negative: "-";
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].symbols); // "◰ ◳ ◲ ◱"
```

## توصیه‌ها

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
