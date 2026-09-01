---
title: "CSSStyleRule: styleMap property"
short-title: styleMap
slug: Web/API/CSSStyleRule/styleMap
page-type: web-api-instance-property
browser-compat: api.CSSStyleRule.styleMap
---

{{APIRef("CSSOM")}}

خاصیت فقطخواندنی **`styleMap`** در رابط {{domxref("CSSStyleRule")}} یک شیء {{domxref('StylePropertyMap')}} برمیگرداند که دسترسی به جفتهای ویژگی-مقدار قانون را فراهم میکند.

## مقدار

یک شیء {{domxref('StylePropertyMap')}}.

## مثال

مثال زیر نشان میدهد که چگونه از `styleMap` برای تغییر یک استایل با استفاده از متد {{domxref('StylePropertyMap.set()')}} استفاده میشود.

```js
const stylesheet = document.styleSheets[0];

Object.values(stylesheet.cssRules).forEach((block) => {
  if (block.selectorText === "button") {
    block.styleMap.set("--main-color", "black");
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}