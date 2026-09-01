```yaml
---
title: CSSSupportsRule
slug: Web/API/CSSSupportsRule
page-type: web-api-interface
browser-compat: api.CSSSupportsRule
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSSupportsRule`** نمایانگر یک قانون‌های فرعی {{cssxref("@supports")}} در CSS است (یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)).

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از اجداد خود {{domxref("CSSConditionRule")}}، {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

## روش‌های نمونه

_روش‌ها را از اجداد خود {{domxref("CSSConditionRule")}}، {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

CSS شامل یک پرس‌وجوی ویژگی (feature query) با استفاده از قانون فرعی {{cssxref("@supports")}} است که یک قانون سبک را در خود دارد. این اولین `CSSRule` خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود. بنابراین `myRules[0]` یک شیء `CSSSupportsRule` را برمی‌گرداند.

```css
@supports (display: grid) {
  body {
    color: blue;
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0]); // یک CSSSupportsRule که نشان‌دهندهٔ پرس‌وجوی ویژگی است.
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@supports")}}
```