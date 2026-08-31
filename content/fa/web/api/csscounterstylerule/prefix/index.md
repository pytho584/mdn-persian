---
title: "CSSCounterStyleRule: prefix property"
short-title: prefix
slug: Web/API/CSSCounterStyleRule/prefix
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.prefix
---

{{APIRef("CSSOM")}}

ویژگی **`prefix`** از رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیفگر {{cssxref("@counter-style/prefix","prefix")}} را می‌خواند و تنظیم می‌کند. اگر برای این توصیفگر مقداری تعیین نشده باشد، این ویژگی یک رشته خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همان قانون `@counter-style` است و دریافت `prefix` مقدار `"Chapter "` را به ما می‌دهد.

```css
@counter-style chapters {
  system: numeric;
  symbols: "0" "1" "2" "3" "4" "5" "6" "7" "8" "9";
  prefix: "Chapter ";
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].prefix); // "Chapter "
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}