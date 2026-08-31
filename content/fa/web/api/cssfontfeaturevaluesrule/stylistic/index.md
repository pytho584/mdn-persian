---
title: "CSSFontFeatureValuesRule: stylistic property"
short-title: stylistic
slug: Web/API/CSSFontFeatureValuesRule/stylistic
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesRule.stylistic
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **stylistic** در رابط {{domXRef("CSSFontFeatureValuesRule")}} حاوی یک {{domXRef("CSSFontFeatureValuesMap")}} است که [شناسه سفارشی تعریف‌شده توسط کاربر](/en-US/docs/Web/CSS/Reference/Values/custom-ident) و [شاخص ویژگی](/en-US/docs/Web/CSS/Reference/Properties/font-feature-settings#optional_value) را برای فونت متغیری که از {{CSSXRef("font-variant-alternates", "stylistic()", "#stylistic")}} پشتیبانی می‌کند، نمایش می‌دهد.

## مقدار

یک شیء {{domxref("CSSFontFeatureValuesMap")}}.

اگرچه خود ویژگی `stylistic` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `CSSFontFeatureValuesMap` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `stylistic` مقداردهی کنید. همچنین می‌توانید مقادیر `stylistic` را با استفاده از [متدهای نمونه `CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap#instance_methods) تغییر دهید.

## مثال

### استفاده پایه

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @stylistic {
    my-stylistics: 1;
  }
}
```

#### JavaScript

```js
// look for the first stylesheet and the first cssRule in that sheet
const myRule = document.styleSheets[0].cssRules[0];
// check
if (myRule instanceof CSSFontFeatureValuesRule && myRule.stylistic.size) {
  // do something with the stylistic
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxRef("@font-feature-values","@stylistic","#stylistic")}}
- نشانه‌گذاری تابعی {{cssxRef("font-variant-alternates","stylistic()","#stylistic")}}
- {{domxref("CSSFontFeatureValuesMap")}}
