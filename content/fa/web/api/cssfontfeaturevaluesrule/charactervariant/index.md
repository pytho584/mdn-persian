---
title: "CSSFontFeatureValuesRule: characterVariant property"
short-title: characterVariant
slug: Web/API/CSSFontFeatureValuesRule/characterVariant
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesRule.characterVariant
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **characterVariant** در رابط {{domXRef("CSSFontFeatureValuesRule")}} یک شیء {{domXRef("CSSFontFeatureValuesMap")}} را نگه می‌دارد که [شناسه تعریف‌شده توسط کاربر](/en-US/docs/Web/CSS/Reference/Values/custom-ident) و [اندیس ویژگی](/en-US/docs/Web/CSS/Reference/Properties/font-feature-settings#optional_value) را برای فونت متغیری که از {{CSSXRef("font-variant-alternates", "character-variant()", "#character-variant")}} پشتیبانی می‌کند، نشان می‌دهد.

## مقدار

یک شیء {{domxref("CSSFontFeatureValuesMap")}}.

اگرچه خود ویژگی `characterVariant` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `CSSFontFeatureValuesMap` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `characterVariant` مقداردهی کنید. همچنین می‌توانید با استفاده از [متدهای نمونه `CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap#instance_methods) مقادیر `characterVariant` را تغییر دهید.

## مثال‌ها

### استفاده پایه

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @character-variant {
    my-character-variant: 1;
  }
}
```

#### جاوااسکریپت

```js
// look for the first stylesheet and the first cssRule in that sheet
const myRule = document.styleSheets[0].cssRules[0];
// check
if (
  myRule instanceof CSSFontFeatureValuesRule &&
  myRule.characterVariant.size
) {
  // do something with the characterVariant
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{cssxRef("@font-feature-values","@character-variant","#character-variant")}}
- نشانه‌گذاری تابعی {{cssxRef("font-variant-alternates","character-variant()","#character-variant")}}
- {{domxref("CSSFontFeatureValuesMap")}}