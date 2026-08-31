---
title: "CSSCounterStyleRule: additiveSymbols property"
short-title: additiveSymbols
slug: Web/API/CSSCounterStyleRule/additiveSymbols
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.additiveSymbols
---

{{APIRef("CSSOM")}}

خاصیت **`additiveSymbols`** از رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیف‌گر {{cssxref("@counter-style/additive-symbols","additive-symbols")}} را دریافت و تنظیم می‌کند. اگر توصیف‌گر مقداری تعیین نکرده باشد، این ویژگی یک رشته خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همین قانون `@counter-style` است و `additiveSymbols` مقدار `" V 5, IV 4, I 1"` را برمی‌گرداند.

```css
@counter-style additive-symbols-example {
  system: additive;
  additive-symbols:
    V 5,
    IV 4,
    I 1;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].additiveSymbols); // " V 5, IV 4, I 1"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}