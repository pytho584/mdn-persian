---
title: "CSSPositionTryRule: name property"
short-title: name
slug: Web/API/CSSPositionTryRule/name
page-type: web-api-instance-property
browser-compat: api.CSSPositionTryRule.name
---

{{APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("CSSPositionTryRule")}}، نام گزینهٔ جایگزین موقعیت (position try fallback option) را نشان می‌دهد که توسط {{cssxref("dashed-ident")}} قاعدهٔ at-rule «@position-try» تعیین شده است.

## مقدار

یک رشته (string).

## مثال‌ها

کد CSS شامل یک قاعدهٔ at-rule «@position-try» با نام `--custom-bottom` و سه توصیفگر است.

```css
@position-try --custom-bottom {
  top: anchor(bottom);
  min-width: 100px;
  margin-top: 10px;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
const tryOption = myRules[0]; // a CSSPositionTryRule
console.log(tryOption.name); // "--custom-bottom"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("CSSPositionTryDescriptors")}}
- {{cssxref("@position-try")}}
- {{cssxref("position-try-fallbacks")}}
- ماژول [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning)
- [Using CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
- [Handling overflow: try options and conditional hiding](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding)