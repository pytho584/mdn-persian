---
title: CSSPositionTryRule
slug: Web/API/CSSPositionTryRule
page-type: web-api-interface
browser-compat: api.CSSPositionTryRule
---

{{APIRef("CSSOM")}}

رابط **`CSSPositionTryRule`** شیئی را توصیف می‌کند که نمایانگر یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{cssxref("@position-try")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌هایی را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSPositionTryRule.name")}} {{ReadOnlyInline}}
  - : نمایانگر نام گزینه‌ی موقعیت‌یابی (position try option) است که توسط {{cssxref("dashed-ident")}} در at-rule `@position-try` مشخص شده است.
- {{domxref("CSSPositionTryRule.style")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("CSSPositionTryDescriptors")}} که نمایانگر اعلان‌های (declarations) تنظیم شده در بدنه‌ی at-rule `@position-try` است.

## روش‌های نمونه

_روش‌های خاصی ندارد؛ روش‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

CSS شامل یک at-rule از نوع `@position-try` با نام `--custom-left` و سه توصیف‌گر (descriptor) است.

```css
@position-try --custom-left {
  position-area: left;
  width: 20%;
  max-width: 200px;
  margin-right: 10px;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
const tryOption = myRules[0]; // a CSSPositionTryRule
console.log(tryOption); // "[object CSSPositionTryRule]"
console.log(tryOption.name); // "--custom-left"
console.log(tryOption.style); // "[object CSSPositionTryDescriptors]"
console.log(tryOption.style.maxWidth); // "200px"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMxRef("CSSPositionTryDescriptors")}}
- {{cssxref("@position-try")}}
- {{cssxref("position-try-fallbacks")}}
- ماژول [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning)
- [Using CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
- [Handling overflow: try options and conditional hiding](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding)