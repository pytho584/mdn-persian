---
title: "CSSCounterStyleRule: range property"
---

---
title: "CSSCounterStyleRule: range property"
short-title: range
slug: Web/API/CSSCounterStyleRule/range
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.range
---

{{APIRef("CSSOM")}}

خاصیت **`range`** در رابط {{domxref("CSSCounterStyleRule")}} مقدار توصیفگر {{cssxref("@counter-style/range","range")}} را خوانده و تنظیم می‌کند. اگر برای این توصیفگر مقداری تعیین نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` همین قانون `@counter-style` است و فراخوانی `range` مقدار `"2 4, 7 9"` را برمی‌گرداند.

```css
@counter-style range-multi-example {
  system: cyclic;
  symbols: "\25A0" "\25A1";
  range:
    2 4,
    7 9;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].range); // "2 4, 7 9"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}