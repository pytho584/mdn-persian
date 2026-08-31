---
title: "CSSCounterStyleRule: name property"
short-title: name
slug: Web/API/CSSCounterStyleRule/name
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.name
---

{{APIRef("CSSOM")}}

ویژگی **`name`** در رابط {{domxref("CSSCounterStyleRule")}}، {{CSSxRef("&lt;custom-ident&gt;")}} تعریف‌شده به عنوان `name` برای قانون مرتبط را دریافت و تنظیم می‌کند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک قانون {{cssxref("@counter-style")}} را نشان می‌دهد. در جاوااسکریپت، `myRules[0]` این قانون `@counter-style` است و بازگرداندن `name` شناسه سفارشی "box-corner" را به ما می‌دهد.

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
console.log(myRules[0].name); // "box-corner"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}