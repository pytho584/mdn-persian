---
title: "CSSFontFeatureValuesMap: size property"
short-title: size
slug: Web/API/CSSFontFeatureValuesMap/size
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.size
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

خصوصیت فقط خواندنی **`size`** در رابط {{domxref("CSSFontFeatureValuesMap")}} یک عدد صحیح مثبت شامل اندازه شیء `CSSFontFeatureValuesMap` را برمی‌گرداند.

## مقدار

یک عدد صحیح مثبت.

## مثال‌ها

### استفاده پایه

مثال زیر یک عدد صحیح از تعداد اعلان‌های داخل بلوک ویژگی [`@swash`](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#swash) را خروجی می‌دهد. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقادیر ویژگی‌ها](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @swash {
    swishy: 1;
    swashy: 2;
  }
}
```

#### جاوااسکریپت

```js
// get the rules
const myRule = document.styleSheets[0].cssRules[0];
console.log(myRule.swash.size); // logs 2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}