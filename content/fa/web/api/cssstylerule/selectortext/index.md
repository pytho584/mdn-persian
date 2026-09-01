---
title: "CSSStyleRule: selectorText property"
short-title: selectorText
slug: Web/API/CSSStyleRule/selectorText
page-type: web-api-instance-property
browser-compat: api.CSSStyleRule.selectorText
---

{{APIRef("CSSOM")}}

ویژگی **`selectorText`** از واسط {{domxref("CSSStyleRule")}}، انتخابگرهای مرتبط با `CSSStyleRule` را دریافت و تنظیم می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

CSS شامل یک قانون استایل است. این قانون اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود. بنابراین `myRules[0].selectorText` یک رشته تحت‌اللفظی از انتخابگر را برمی‌گرداند که در اینجا `"h1"` است.

```css
h1 {
  color: pink;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].selectorText); // یک رشته حاوی "h1".
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}