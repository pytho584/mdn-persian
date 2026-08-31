---
title: "CSSCounterStyleRule: negative property"
---

---
title: "CSSCounterStyleRule: negative property"
short-title: negative
slug: Web/API/CSSCounterStyleRule/negative
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.negative
---

{{APIRef("CSSOM")}}

ویژگی **`negative`** از رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیفگر {{cssxref("@counter-style/negative","negative")}} را دریافت و تنظیم می‌کند. اگر برای این توصیفگر مقداری تعیین نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همین قانون `@counter-style` است و فراخوانی `negative` مقدار «-» را به ما می‌دهد.

```css
@counter-style neg {
  system: numeric;
  symbols: "0" "1" "2" "3" "4" "5" "6" "7" "8" "9";
  negative: "-";
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].negative); // "-"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}