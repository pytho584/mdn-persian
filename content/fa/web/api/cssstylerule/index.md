---
title: CSSStyleRule
slug: Web/API/CSSStyleRule
page-type: web-api-interface
browser-compat: api.CSSStyleRule
---

{{ APIRef("CSSOM") }}

رابطِ **`CSSStyleRule`** یک قانون استایلِ تکیِ CSS را نمایش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والدهای خود، یعنی {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSStyleRule.selectorText")}}
  - : نمایش متنی انتخابگر (selector) این قانون را برمی‌گرداند؛ مثلاً `"h1, h2"`.
- {{domxref("CSSStyleRule.style")}} {{ReadOnlyInline}}
  - : شیء {{domxref("CSSStyleProperties")}} مربوط به این قانون را برمی‌گرداند که استایل‌های آن را نشان می‌دهد.
- {{domxref("CSSStyleRule.styleMap")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('StylePropertyMap')}} برمی‌گرداند که به جفت‌های ویژگی-مقدارِ این قانون دسترسی می‌دهد.

## روش‌های نمونه

_روش‌ها را از والدهای خود، یعنی {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

### دریافت یک قانون استایل

CSS زیر قانون استایل مربوط به انتخابگرِ `h1` را تعریف می‌کند که در کد با یک نمونه از `CSSStyleRule` نمایش داده می‌شود.

```css
h1 {
  color: pink;
}
```

با فرض اینکه قانون استایل بالا اولین قانون در سند باشد، اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` برگردانده می‌شود. عبارت `myRules[0].style` یک شیء {{domxref("CSSStyleProperties")}} برمی‌گرداند که اعلان‌های تعریف‌شده برای `h1` را نشان می‌دهد.

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0]); // یک CSSStyleRule که نمایانگر h1 است.
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}