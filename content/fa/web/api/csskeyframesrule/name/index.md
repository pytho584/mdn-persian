---
title: "CSSKeyframesRule: name property"
short-title: name
slug: Web/API/CSSKeyframesRule/name
page-type: web-api-instance-property
browser-compat: api.CSSKeyframesRule.name
---

{{APIRef("CSSOM") }}

ویژگی **`name`** در رابط {{domxref("CSSKeyframeRule")}} نام انیمیشن را که توسط ویژگی {{cssxref("animation-name")}} استفاده میشود، دریافت و تعیین میکند.

## مقدار

یک رشته (string).

## مثالها

CSS شامل یک at-rule کلیدفریم (keyframes) است. این at-rule اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده میشود.
`myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} برمیگرداند که `name` آن برابر با `"slide-in"` است.

```css
@keyframes slide-in {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
let keyframes = myRules[0]; // a CSSKeyframesRule
console.log(keyframes.name); // "slide-in"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}