---
title: "CSSRule: parentRule property"
short-title: parentRule
slug: Web/API/CSSRule/parentRule
page-type: web-api-instance-property
browser-compat: api.CSSRule.parentRule
---

{{ APIRef("CSSOM") }}

خاصیت **`parentRule`** از رابط {{domxref("CSSRule")}}، در صورت وجود، قاعدهٔ شاملِ قاعدهٔ فعلی را بازمیگرداند؛ در غیر این صورت `null` برمیگرداند.

## مقدار

یک {{domxref("CSSRule")}} که نوع قاعدهٔ شامل است. اگر قاعدهٔ فعلی داخل یک media query باشد، این خاصیت یک {{domxref("CSSMediaRule")}} برمیگرداند. در غیر این صورت `null` برمیگرداند.

## مثال‌ها

```css
@media (width >= 500px) {
  .box {
    width: 100px;
    height: 200px;
    background-color: red;
  }

  body {
    color: blue;
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
let childRules = myRules[0].cssRules;
console.log(childRules[0].parentRule); // a CSSMediaRule
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}