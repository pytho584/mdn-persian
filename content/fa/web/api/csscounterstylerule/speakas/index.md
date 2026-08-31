---
title: "CSSCounterStyleRule: speakAs property"
short-title: speakAs
slug: Web/API/CSSCounterStyleRule/speakAs
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.speakAs
---

{{APIRef("CSSOM")}}

ویژگی **`speakAs`** از رابط {{domxref("CSSCounterStyleRule")}}، مقدار توصیفگر {{cssxref("@counter-style/speak-as","speak-as")}} را دریافت و تنظیم می‌کند. اگر برای این توصیفگر مقداری تنظیم نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همین قانون `@counter-style` است و `speakAs` مقدار «bullets» را به ما می‌دهد.

```css
@counter-style box-corner {
  system: fixed;
  symbols: ◰ ◳ ◲ ◱;
  suffix: ": ";
  speak-as: bullets;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].speakAs); // "bullets"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}